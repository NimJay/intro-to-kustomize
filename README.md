# Intro to Kustomize

This repository contains introductory example code for [Kustomize](https://kustomize.io/). Kustomize is a command-line tool built into `kubectl`. Kustomize allows you to maintain multiple variants of a bunch of Kubernetes resources without YAML duplication.

## Instructions

Here's how you should use this repository:

**1.** Look at the following diagram.

![A diagram of 2 Pods labeled "pod-label: my-pod", in a Deployments called my-deployment, in a Service called my-service.](https://raw.githubusercontent.com/NimJay/intro-to-kustomize/main/pods-deployment-service-diagram.png)

The diagram depicts the "base" set of Kubernetes resources this repository works with:
* 1 `Service` of `type: LoadBalancer` which will allow public ingress.
* 1 `Deployment` containing 2 instances (`replicas: 2`) of a `Pod`.
* Each `Pod` just runs a Docker container of a "Hello, world!" app.

The `Deployment` runs 2 instances (`replicas: 2`) of a `Pod`.

**2.** Explore the YAML in the `base/` folder.

**3.** Explore each of the other folders. Each folder contains a `kustomization.yaml` that demonstrates the use of a specific [Kustomize Transformer or Generator](https://kubectl.docs.kubernetes.io/references/kustomize/builtins/).

**4.** Build each `kustomization.yaml` using the instructions below.


## Build an Example

To view the `kustomize build` output of an example, you do **not** need to install `kustomize` separately. 
`kustomize build` is built into `kubectl`. Use:
```
kubectl kustomize <path-to-folder>
```

## Deploy an Example

To deploy the resources to your Kubernetes cluster, use:
```
kubectl apply -k <path-to-folder>
```

### Remove an Example

To remove the resources deloyed to your Kubernetes cluster, use:
```
kubectl delete -k <path-to-folder>
```

## Additional Resources

For further reading, check out the official [Kustomize references](https://kubectl.docs.kubernetes.io/references/kustomize/).
For instance, check out the [reference documentation for `commonAnnotations`](https://kubectl.docs.kubernetes.io/references/kustomize/kustomization/commonannotations/).
