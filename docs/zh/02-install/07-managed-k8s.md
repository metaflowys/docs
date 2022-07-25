---
title: 监控托管 K8s 集群
permalink: /install/managed-k8s
---

# 简介

DeepFlow 支持监控云服务商的托管 K8s 集群。与[直接监控 K8s 集群](./single-k8s/)的唯一区别是，通过调用云厂商 API，可自动向观测数据中注入云资源的标签（AutoTagging）。

# 部署拓扑

```mermaid
flowchart TD

subgraph VPC
  subgraph Managed-K8s-Cluster
    APIServer["k8s apiserver"]
    DeepFlowAgent["deepflow-agent (daemonset)"]
    DeepFlowServer["deepflow-server (statefulset)"]

    DeepFlowAgent -->|"get k8s resource & label"| APIServer
    DeepFlowAgent -->|"control & data"| DeepFlowServer
  end
end

DeepFlowServer -->|"get cloud resource & label"| CloudAPI[cloud api service]
```

# 配置 DeepFlow Server

TODO

# 部署 DeepFlow Agent

TODO

# 下一步

- [微服务全景图 - 体验 DeepFlow 基于 BPF 的 AutoMetrics 能力](../auto-metrics/metrics-without-instrumentation/)
- [自动分布式追踪 - 体验 DeepFlow 基于 eBPF 的 AutoTracing 能力](../auto-tracing/tracing-without-instrumentation/)
- [消除数据孤岛 - 了解 DeepFlow 的 AutoTagging 和 SmartEncoding 能力](../auto-tagging/elimilate-data-silos/)
- [告别高基烦恼 - 集成 Promethes 等指标数据](../agent-integration/metrics/metrics-auto-tagging/)
- [无缝分布式追踪 - 集成 OpenTelemetry 等追踪数据](../agent-integration/tracing/tracing-without-blind-spot/)
