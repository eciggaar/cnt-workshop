# Create an application

If everything went fine in the previous step, you should already be logged on to the OpenShift cluster that has been assigned to you as part of the workshop. To double-check, switch tab to the Cloud Shell and type:

```bash
$ oc project
```
This should list the currently active project. If you receive the error message telling that you are not logged on, complete the steps in the 

## Create the development namespace

Before getting started, the development namespace/project needs to be created and prepared for the DevOps pipelines. This is something that would typically happen once at the beginning of a project when a development team is formed and assigned to the cluster.

This step copies the common secrets and configMaps that contain the CI/CD configuration from the tools namespace into the development namespace/project. This enables the pipelines to reference the values easily for your project. To create such your own development namespace, switch tab to a Cloud Shell and type:

```bash
$ oc sync ${DEV_NAMESPACE}
```

where `${DEV_NAMESPACE}` is the name you've chosen for your development namespace/project.

## Open the Developer Dashboard

The Developer Dashboard makes it easy for you to navigate to the tools, including a section that allows you to select a set of preconfigured Starter Kits that make seeding your development project very easy.

Before starting, open a browser and make sure you are logged into Github. Next, navigate to the OpenShift web console and open the Application Launcher dropdown from the top-right (1) and select Developer Dashboard (2).

![Developer Dashboard](images/developer-dashboard.png)

## Create your app in Git

---
**Warning**

Your browser needs to be logged in to your GitHub account for a template to work. If the link from the tile displays the GitHub 404 page, log in and reload the page.

---

1. From the Developer Dashboard, click on the **Starter Kits** tab.

2. Pick one of the templates that is a good architectural fit for your application and the language and framework that you prefer to work with. For your first application, select the **Typescript Microservice**. This also works well in the Cloud Shell and is perfect for this workshop.

    Click on a Starter Kit **Tile** to create your app github repository from the template repository selected. 

    You can also click on the Git Icon to browse the source template repository and click on the Template to create the template.

3. Next, complete the GitHub create repository from template process.

    * **Owner**: Select a valid GitHub organization that you are authorized to create repositories within.
    * **Repository name**: Enter a name for your repo. GitHub will help with showing a green tick if it is valid (See warning above)
    * **Description**: Describe your app

    Press **Create repository from template**

    ![Create Repository from Template](images/create-repo-from-template.png)

    The new repository will be created in your selected organization.

---

__Continue with the next part [Create the DevOps pipeline](3-Pipelines.md)__
