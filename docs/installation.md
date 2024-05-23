# Installation

## Prerequisites

### Kubernetes or OpenShift cluster

First, you'll need a recentish Kubernetes or OpenShift
cluster. Additionally, your cluster should have nodes with Nvidia GPUs
available. At least one Nvidia A10 sized GPU should be available for
basic testing, but you'll want Nodes with multiple A10 or A100 GPUs do
handle multi-GPU training and inference for larger models. Every node
does not have to be GPU-enabled, but you should have at least 1
GPU-enabled node before moving on

AWS g5.4xlarge, g5.48xlarge, and p4d.24xlarge have been tested and
known to work. If you have to choose just one type to start that is a
good balance between price and performance, g5.48xlarge is
recommended.

Also ensure you have either `kubectl` or `oc` binaries for interacting
with your Kubernetes/OpenShift installed locally to follow along with
the rest of this document.

### Tekton or OpenShift Pipelines

Labrakates requires either a Kubernetes cluster with [Tekton Pipelines
installed](https://tekton.dev/docs/installation/) or an OpenShift
cluster with [OpenShift Pipelines
installed](https://docs.openshift.com/pipelines/1.14/install_config/installing-pipelines.html).

### Persistent Volumes

You'll need the ability to create some persistent volumes in your
cluster. How much space you'll need depends on a few factors, but
ideally you'd have at least 500GB of storage available to allocate to
persistent volumes.

### S3-Compatible Object Storage

Generated synthetic data and training results get stored to
S3-compatible object storage. The generated training data can be quite
small, but the training results can easily run into the dozens,
hundreds, or thousands of GBs depending on the size of models in use.
