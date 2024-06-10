# Sample dotnet app with Tekton pipelines

This is a simple demo on the capabilities of tekton and how it can be used for .net 8 applications.

## Usage

Pipelines are stored on the `.tekton` folder. Normally you'd store common `Task` and `Pipeline` objects in a public repository, and store the `PipelineRun` in the repo.

You'll need a way to push to a remote container registry for this application to work. If you are using Azure Container Registry for this, don't forget to include the required secret on the `ServiceAccount` running the pipelines (normally called `pipeline`) as per [this](https://learn.microsoft.com/en-us/azure/openshift/howto-use-acr-with-aro) guide.

A quick and dirty way of running these while testing (and ONLY while testing) is via this command:

```bash
cd .tekton
oc delete pr --all && oc apply -f dotnetBuildAndPushImage.yaml && oc apply -f simple-pipeline.yaml && oc create -f pipelinerun.yaml
```
