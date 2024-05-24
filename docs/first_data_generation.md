# Your first data generation



```
kubectl kustomize \
  https://github.com/labrakates/pipelines//pipelineruns/generate/ \
  | grep -v "name: ilab-generate-pipelinerun" \
  | kubectl create -f -
```

Forgive the gnarly command - it works around Kustomize not supporting
`generateName` properly and requiring a fixed name value for every
Kubernetes resource.
