# Creating the Pipelines

To allow easy customization of the pipeline as-needed for your
environment, Labrakates uses
[Kustomize](https://kustomize.io/). However, you can ignore that until
it comes time to customize the `Pipeline` or `PipelineRun` resources
you want to create.

To install all the necessary Tekton Task and Pipeline objects into
your current Kubernetes namespace:

```
kubectl apply -k https://github.com/labrakates/pipelines?ref=main
```

**Note**: If using OpenShift, just substitute `oc` for `kubectl` in
the above command.


If all goes well, you should see output like below:

```
$ kubectl apply -k https://github.com/labrakates/pipelines?ref=main
pipeline.tekton.dev/ilab-generate created
pipeline.tekton.dev/ilab-train created
task.tekton.dev/ilab-generate created
task.tekton.dev/ilab-train created
task.tekton.dev/ilab-train-deepspeed created
task.tekton.dev/pull-from-s3 created
task.tekton.dev/save-to-s3 created
```

Once the Pipelines and Tasks are created, you're ready to move on to
your first PipelineRun.
