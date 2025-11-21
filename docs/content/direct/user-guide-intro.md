# KubeStellar User Guide

This document is an overview of the User Guide.
See the KubeStellar [overview](https://github.com/kubestellar/kubestellar/blob/main/README.md) for architecture and other information.

This user guide is an ongoing project. If you find errors, please point them out in our [Slack channel](https://cloud-native.slack.com/archives/C097094RZ3M/) or open an issue in our [github repository](https://github.com/kubestellar/kubestellar)!

## Simple Examples

If you want to try a simple installation process and example then you can try out [Getting Started](get-started.md), which uses [kind](https://kind.sigs.k8s.io/) and a helm chart. The [helm chart](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/core-chart.md) supports many options; the instructions on the Getting Started page show only the chart's usage in that recipe.

Another simple example, which starts with (a slightly modified version of) the OCM Quick Start is [here](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/start-from-ocm.md).

## In Brief

If you want a simple rough grouping, you can divide the concepts here into:

- "setup" (steps 1--7 below), exemplified in [the Setup section of Getting Started](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/get-started.md#setup), and
- "usage" (the remaining steps), illustrated by [the example scenarios document](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/example-scenarios.md).

However, you do not need to follow that dichotomy. As noted below, the relevant components can be organized more flexibly.

## The Full Story

Installing and using KubeStellar progresses through the following steps.

1. Install software prerequisites. See [prerequisites](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/pre-reqs.md).
2. Acquire the ability to use a Kubernetes cluster to serve as the [KubeFlex](https://github.com/kubestellar/kubeflex/) hosting cluster. See [Acquire cluster for KubeFlex hosting](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/acquire-hosting-cluster.md).
3. [Initialize that cluster as a KubeFlex hosting cluster](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/init-hosting-cluster.md).
4. [Inventory and Transport Space](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/its.md) (ITS).
    1. Create something to serve as ITS.
    1. Register the ITS as a KubeFlex ControlPlane.
5. [Workload Description Space](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wds.md) (WDS).
    1. Create something to serve as WDS.
    1. Register the WDS as a KubeFlex ControlPlane and initialize it for KubeStellar usage.
6. Create a [Workload Execution Cluster](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wec.md) (WEC).
7. [Register the WEC in the ITS](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wec-registration.md).
8. Maintain workload desired state in the WDS.
9. Maintain [control objects](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/control.md) in the WDS to bind workload with WEC and modulate the state propagation back and forth. The [API reference](https://pkg.go.dev/github.com/kubestellar/kubestellar/api/control/v1alpha1) documents all of them. There are control objects for the following topics.
    1. [Binding workload with WEC(s)](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/binding.md).
    1. [Transforming desired state](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/transforming.md) as it travels from WDS to WEC.
    1. [Summarizing reported state](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/combined-status.md) from WECs into WDS.
10. Enjoy the effects of workloads being propagated to the WEC.
11. Consume reported state from WDS.

By "maintain" we mean create, read, update, delete, list, and watch as you like, over time. KubeStellar is eventually consistent: you can change your inputs as you like over time, and KubeStellar continually strives to achieve what you are currently asking it to do.

There is some flexibility in the ordering of those steps. The following flowchart shows the key ordering constraints. 

![Ordering among installation and usage actions](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/images/usage-outline.svg)

You can have multiple ITSes, WDSes, and WECs, created and deleted over time as you like.

Besides "Start", the other green items in that graph are entry points for extending usage at any later time. You could also see them as distinct user roles or authorities, or as additional layers of setup/install.

KubeStellar's [Core Helm chart](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/core-chart.md) combines (a) initializing the KubeFlex hosting cluster, (b) optionally creating and certainly registering some ITSes, and (c) optionally creating and certainly registering and initializing some WDSes.

You can find an example run through of steps 2--7 in [Getting Started](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/get-started.md). This dovetails with [the example scenarios document](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/example-scenarios.md), which shows examples of the later steps.

There is also an example run through of steps 2--7 that starts with (a slightly modified version of) the OCM Quick Start and also dovetails with the example scenarios. See [here](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/start-from-ocm.md).

## Observability and Monitoring

KubeStellar provides several endpoints and integrations for observability, including Prometheus metrics and debug endpoints. See the [Observability](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/observability.md) page for details on available metrics, endpoints, and how to access them.

## Troubleshooting

See [the Troubleshooting guide](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/troubleshooting.md).

## Teardown

See [Teardown](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/teardown.md) for how to tear everything down to unadorned Kubernetes clusters.
