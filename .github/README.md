## Azure Container Instances (ACI), FROM scratch

This is an extension of my [Docker, FROM scratch](https://github.com/aaronpowell/docker-from-scratch) workshop but using [Azure Container Instances](https://docs.microsoft.com/en-us/azure/container-instances/?wt.mc_id=acifromscratch-github-aapowelll) rather than a local Docker host.

The exercises have been optimised to run from [Visual Studio Code (VSCode)](https://code.visualstudio.com?wt.mc_id=acifromscratch-github-aapowell) but can be run from any command line, just make sure you refer script files in each exercise, and each branch represents a new exercise.

## Setting up your environment

* You'll need is an Azure account, you can [sign up for a free trial](https://azure.microsoft.com/en-us/free/?wt.mc_id=acifromscratch-github-aapowell) if you don't have an account.
* You can either use the [Azure Cloud Shell](https://shell.azure.com/?wt.mc_id=acifromscratch-github-aapowell) or install the [Azure cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) (or use it in a [Docker container](https://docs.microsoft.com/en-us/cli/azure/run-azure-cli-docker?view=azure-cli-latest&wt.mc_id=acifromscratch-github-aapowell) if you like!)
  * The `az --version` at time of creation is **2.0.59**

## Exercises

In this exercise we'll look at connecting our container to another Azure resource, an [Azure SQL Server](https://azure.microsoft.com/en-us/services/sql-database/?wt.mc_id=acifromscratch-github-aapowell).

The script for this exercise is [run.azcli](./run.azcli) and contains a number of commands that we'll execute using the `az` cli and the application is a .NET Core web application that lives in the `src` (don't worry, you don't need .NET installed, we'll do it all in Docker!).

We'll create an Azure SQL Server and Database using `az sql` and then make it available to our container by white-listing all Azure IP addresses using a the SQL firewall command `az sql server firewall-rule`.

_Note: The application will automatically create the database schema on start, you won't need to do it manually._