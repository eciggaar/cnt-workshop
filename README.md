# How to build a modern CI/CD workflow with Tekton on OpenShift, Part 1

## Learning objectives

This workshop is all about creating and deploying a Quarkus application as a Knative service on OpenShift using a modern CI/CD workflow. It is inspired on two great existing blogs on this topic, written by David Sancho --- see the [Resources](#resources) section below for the links. In this first part of the workshop, we will focus on setting up a Tekton pipeline and how to use it to deploy a simple Quarkus application.

It more detail, this part of the workshop covers:

1. Prerequisites (access to an OpenShift cluster, work environment, etc.)

1. Installing the required OpenShift Operators

1. Create an OpenShift Pipeline and deploy your Quarkus application with it

1. Make a change to the application and get this deployed using the pipeline

1. Leverage Traffic Management to test your new changes

1. Auto-Scaling (optional)

Click the link below to get started & have fun!! Happy coding :smiley:

---

**[Let's get started with the hands-on part!!](openshift/1-Prereqs.md)**

---

To complete this workshop, a basic understanding of Kubernetes/OpenShift, Tekton pipelines and application deployment on OpenShift is instrumental!

## Tools

In this workshop we will be using the IBM Cloud Shell which has all required tools installed.

Should you prefer to run the workshop completely off your own workstation you need the following tools.

Tool  |Source       
----------------|----
git CLI|https://git-scm.com/downloads 
ibmcloud CLI|https://cloud.ibm.com/docs/cli?opic=cli-install-ibmcloud-cli
ibmcloud plugin|https://cloud.ibm.com/docs/cli?topic=cli-plug-ins -- Install kubernetes-service plugin
oc|Download from OpenShift Web Console, click on question mark
kn|https://knative.dev/docs/install/install-kn/
hey|HTTP Load generator: https://github.com/rakyll/hey

## Resources

You can find detailed information and learn more about Knative here:

1. [Building modern CI/CD workflows for serverless applications with Red Hat OpenShift Pipelines and Argo CD, Part 1](https://developers.redhat.com/blog/2020/10/01/building-modern-ci-cd-workflows-for-serverless-applications-with-red-hat-openshift-pipelines-and-argo-cd-part-1/)

1. [Building modern CI/CD workflows for serverless applications with Red Hat OpenShift Pipelines and Argo CD, Part 2](https://developers.redhat.com/blog/2020/10/14/building-modern-ci-cd-workflows-for-serverless-applications-with-red-hat-openshift-pipelines-and-argo-cd-part-2/)

1. [Knative documentation](https://knative.dev/docs)

1. [Quarkus Getting Started](https://quarkus.io/get-started/)

1. [Red Hat Knative Tutorial](https://redhat-developer-demos.github.io/knative-tutorial/knative-tutorial/index.html)

