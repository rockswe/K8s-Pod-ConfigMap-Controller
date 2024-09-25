# PodConfigMapController

A custom Kubernetes controller written in Go that watches for Pod events and automatically creates or deletes ConfigMaps containing their metadata. The controller supports:

- **Pod Events**: Handles create, update, and delete events for Pods.
- **ConfigMap Management**: Creates and deletes ConfigMaps corresponding to Pods.
- **Custom Resource Definition (CRD)**: Integrates a CRD for dynamic behavior customization.
- **Leader Election**: Ensures only one active controller instance operates at a time.
- **Prometheus Metrics**: Exposes metrics for monitoring via Prometheus.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Custom Resource Definition (CRD)](#custom-resource-definition-crd)
- [Leader Election](#leader-election)
- [Prometheus Metrics](#prometheus-metrics)
- [Contributing](#contributing)
- [License](#license)

## Introduction

PodConfigMapController automates the management of ConfigMaps based on Pod metadata. It listens to Pod events across all namespaces and ensures that a corresponding ConfigMap is created or deleted when a Pod is created or deleted. The controller can be customized using a CRD and supports leader election for high availability.

## Prerequisites

- **Go**: Version 1.19 or higher.
- **Kubernetes Cluster**: Version 1.28 or compatible.
- **Kubectl**: Configured to communicate with your cluster.
- **Docker**: For containerizing the controller (optional).
- **Kubernetes Code Generator**: If you plan to modify or extend the CRD functionality.

## Installation

### Clone the Repository

```bash
git clone https://github.com/yourusername/PodConfigMapController.git
cd PodConfigMapController
```

### Build The Controller
Ensure you have Go installed and your GOPATH is set up.
```bash
go build -o podconfigmapcontroller main.go
```

### Run the Controller
You can run the controller locally for development purposes or for testing.

#### Running Locally with Kubeconfig
```bash
./podconfigmapcontroller --kubeconfig=/path/to/your/kubeconfig
```
P.S: Replace /path/to/your/kubeconfig with the path to your Kubernetes configuration file. If you're running this within a cluster or the default kubeconfig is sufficient, you can omit the --kubeconfig flag.
