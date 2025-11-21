# Setting up KubeStellar

"Setup" is a porous grouping of some of the steps in [the full outline](user-guide-intro.md#the-full-story), and comprises the following. Also, bear in mind the [Setup limitations](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/setup-limitations.md).

- Install software prerequisites. See [prerequisites](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/pre-reqs.md).
- KubeFlex Hosting cluster
    - Acquire the ability to use a Kubernetes cluster to serve as the [KubeFlex](https://github.com/kubestellar/kubeflex/) hosting cluster. See [Acquire cluster for KubeFlex hosting](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/acquire-hosting-cluster.md).
    - [Initialize that cluster as a KubeFlex hosting cluster](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/init-hosting-cluster.md).
- Core Spaces
    - Create an [Inventory and Transport Space](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/its.md) (ITS).
    - Create a [Workload Description Space](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wds.md) (WDS).
- [Core Helm Chart](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/core-chart.md) (covering three of the above topics).
- Workload Execution Clusters
    - Create a [Workload Execution Cluster](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wec.md) (WEC).
    - [Register the WEC in the ITS](https://github.com/kubestellar/kubestellar/blob/main/docs/content/direct/wec-registration.md).
