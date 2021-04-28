# Knative Traffic Management

In the previous section you have replaced revision v1 of the `quarkus-hello-world` app with revision v2.

What if you want to do a canary release and test the new revision/version on a subset of your users?  

This is something you can easily do with Istio. It requires additional VirtualService and DestinationRule definitions.

Using pipelines and Knative it is also rather simple to accomplish this. Again, a good approach would be to trigger this by adding / changing the configuration in a dedicated Git repository -- as mentioned in the previous section of this workshop. However, in this lab wel will edit the pipeline directly and implicitly create a new pipeline run when starting the pipeline.

1. For this, switch tab to the IBM Cloud Shell and ensure that the `devops-workshop` project is your current project. Then, edit the pipeline by running:
    
    ```bash
    $ oc edit pipeline workshop-pipeline
    ```
    
    The pipeline opens in editing mode with vi as editor. 

1. Now, search for the string `env=GREETING_MESSAGE` by typing `/` followed by:

    ```
    env=GREETING_MESSAGE
    ```

    Hit \<ENTER\> and type `n` once to go the next search result. You should now be at the following line:

    ```
    - --env=GREETING_MESSAGE=Hello DevOps Workshop v2 UPDATE!!!
    ```

1. Switch to editing mode and replace the line `- --env=GREETING_MESSAGE=Hello DevOps Workshop v2 UPDATE!!!` with the following lines:

    ```
    - --env=GREETING_MESSAGE=Hello DevOps Workshop v2 UPDATE!!!
    - --tag=quarkus-hello-world-v1=v1
    - --tag=quarkus-hello-world-v2=v2
    - --traffic=v1=75
    - --traffic=v2=25
    ```

    Furthermore, change `create` into `update` and remove the `--force` flag, so that the `ARGS` parameter of the Knative client invocation looks like:

    ```
    - name: ARGS
      value:
        - service
        - update
        - quarkus-hello-world
        - --image=$(params.image-registry)/$(params.image-repository)/quarkus-hello-world:$(params.source-revision)
        - --revision-name=quarkus-hello-world-v2
        - --env=GREETING_MESSAGE=Hello DevOps Workshop v2 UPDATE!!!
        - --tag=quarkus-hello-world-v1=v1
        - --tag=quarkus-hello-world-v2=v2
        - --traffic=v1=75
        - --traffic=v2=25        
    ```

    Those additional 4 lines of code -- with the `tag` and `traffic` entries -- will create a 75% / 25% distribution between revisions `-v1` and `-v2`.

1. Finally, save your changes by pressing `<Esc>`, followed by type `:wq`. You should see the following output:

    ```
    pipeline.tekton.dev/workshop-pipeline edited
    ```

1. In the Cloud shell, use the Tekton CLI to run the pipeline again:

    ```bash
    $ tkn pipeline start workshop-pipeline -w name=source,claimName=source-pvc -w name=maven-settings,config=maven-settings
    ```

    Accept the defaults again and check the logs or monitor the deployment via the Web Console. Wait for it to successfully complete.
   
1. In the OpenShift Web Console Topology view you can see that now both revisions are activated, v1 with 75 %, v2 with 25 %.
   
    ![canary](images/canary.png)

    Note that with "Set Traffic Distribution" you can actually change the distribution without modifying and redeploying the YAML file.

1. Open the Route in your Browser and click refresh multiple times. You will see output of both revisions, `v1` will show up more often than `v2` though (75 % vs. 25 %).

    Back in the Topology view, you can see pods for both revisions are started.
   
---

__Continue with the next part [Knative Auto-Scaling](5-Scaling.md)__
