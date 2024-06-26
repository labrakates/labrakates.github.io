# Your first data generation


To test data generation, you can kick off the simplest possible data
generation pipeline that points to a default taxonomy repository and
doesn't persist the generated results with a PipelineRun like below.

!!! note

    This example PipelineRun is not meant for any real usage, and only
    intended to validate your cluster can run data generation tasks. If
    your cluster has any special requirements, such as admission controllers,
    you may not be able to run this example as-is without customizations.

Download [generate.yaml](pipelines/pipelineruns/generate/generate.yaml) or
copy/paste it from the code block below into a file locally.

``` { .yaml .copy title="generate.yaml" }
--8<-- "pipelines/pipelineruns/generate/generate.yaml"
```

Start your first data generation pipeline with a command like:
``` { .shell .copy}
kubectl create -f generate.yaml
```


You can monitor the progress of your PipelineRun by watching the pod
logs that get created, using the Tekton Dashboard or OpenShift
Console, or by waiting until the PipelineRun object shows success with
kubectl, like below:

``` { .shell }
$ kubectl get pipelinerun ilab-generate-pipelinerun
NAME                        SUCCEEDED   REASON      STARTTIME   COMPLETIONTIME
ilab-generate-pipelinerun   True        Completed   6m10s       84s
```


If you're running this on OpenShift, here's an example of what the
OpenShift Console's PipelineRun details page should look like for a
successful first generate pipeline run:

![OpenShift PipelineRun details](img/first_generate_pipeline_console.png)


Next, we'll look at how to setup a persistent HuggingFace cache so
that we don't always re-download the models from HuggingFace on each
run and how to persist our generation results so that we can use them
in a subsequent training pipeline.
