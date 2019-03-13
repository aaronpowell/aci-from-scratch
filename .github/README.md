## Azure Container Instances (ACI), FROM scratch

This is an extension of my [Docker, FROM scratch](https://github.com/aaronpowell/docker-from-scratch) workshop but using [Azure Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/?wt.mc_id=acifromscratch-github-aapowelll) rather than a local Docker host.

The exercises have been optimised to run from [Visual Studio Code (VSCode)](https://code.visualstudio.com?wt.mc_id=acifromscratch-github-aapowell) but can be run from any command line, just make sure you refer script files in each exercise, and each branch represents a new exercise.

## Setting up your environment

* You'll need is an Azure account, you can [sign up for a free trial](https://azure.microsoft.com/en-us/free/?wt.mc_id=acifromscratch-github-aapowell) if you don't have an account.
* You can either use the [Azure Cloud Shell](https://shell.azure.com/?wt.mc_id=acifromscratch-github-aapowell) or install the [Azure cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) (or use it in a [Docker container](https://docs.microsoft.com/en-us/cli/azure/run-azure-cli-docker?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) if you like!)
  * The `az --version` at time of creation is **2.0.59**

## Exercise

In this exercise we'll be introduced to the [Azure Container Registry (ACR)](https://azure.microsoft.com/en-us/services/container-registry/?wt.mc_id=acifromscratch-github-aapowell). We'll create an image locally (so you'll need Docker installed) before pushing it to ACR and deploying from ACR to ACI.

The script for this exercise is [run.azcli](./run.azcli) and contains a number of commands that we'll execute using the `az` cli and the application is a .NET Core web application that lives in the `src` (don't worry, you don't need .NET installed, we'll do it all in Docker!).

We'll start by building the Docker image using `docker build` and then create an ACR using `az acr create`.

Next we'll make sure that Docker knows about the registry by logging into it using `az acr login` before we tag and push the image.

Finally we'll create our ACI but specify the image in our registry plus connection information for it to use.