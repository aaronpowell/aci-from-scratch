## Azure Container Instances (ACI), FROM scratch

This is an extension of my [Docker, FROM scratch](https://github.com/aaronpowell/docker-from-scratch) workshop but using [Azure Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/?wt.mc_id=acifromscratch-github-aapowelll) rather than a local Docker host.

The exercises have been optimised to run from [Visual Studio Code (VSCode)](https://code.visualstudio.com?wt.mc_id=acifromscratch-github-aapowell) but can be run from any command line, just make sure you refer script files in each exercise, and each branch represents a new exercise.

## Setting up your environment

* You'll need is an Azure account, you can [sign up for a free trial](https://azure.microsoft.com/en-us/free/?wt.mc_id=acifromscratch-github-aapowell) if you don't have an account.
* You can either use the [Azure Cloud Shell](https://shell.azure.com/?wt.mc_id=acifromscratch-github-aapowell) or install the [Azure cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) (or use it in a [Docker container](https://docs.microsoft.com/en-us/cli/azure/run-azure-cli-docker?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) if you like!)
  * The `az --version` at time of creation is **2.0.59**

## Exercises

In this exercise we'll look at using [Container Groups for ACI](https://docs.microsoft.com/en-us/azure/container-instances/container-instances-container-groups?wt.mc_id=acifromscratch-github-aapowell) to deploy two images into the same ACI. We'll also look at how to use [Azure Resource Manager](https://docs.microsoft.com/en-us/azure/azure-resource-manager/?wt.mc_id=acifromscratch-github-aapowell) for the deployment, rather than just the cli.

The script for this exercise is [run.azcli](./run.azcli) and contains a number of commands that we'll execute using the `az` cli, combined with [azuredeploy.json](./azuredeploy.json) Resource Manager Template. The application is a .NET Core web application that lives in the `src` (don't worry, you don't need .NET installed, we'll do it all in Docker!).

We'll use `az group deployment` to deploy our Resource Manager Template (you'll need to enter the ACR password as a parameter) and then in the portal you'll see two containers running in the same ACI. You'll also notice that you can't access the SQL Server container as that port isn't exposed, only the web servers port.

_Note: The application will automatically create the database schema on start, you won't need to do it manually._