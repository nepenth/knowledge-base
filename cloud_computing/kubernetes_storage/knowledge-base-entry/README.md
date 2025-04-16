## Overview

Kubernetes Persistent Volumes (PVs)
=====================================

### Introduction

Kubernetes Persistent Volumes (PVs) provide a robust framework for managing durable storage in containerized environments. Understanding the concepts of PVs is crucial for effectively managing stateful applications in Kubernetes, ensuring that data persists as needed and storage resources are utilized efficiently.

### Main Concepts

The main concept of PVs is to decouple storage provisioning from Pod management, enabling administrators to manage storage resources separately from application deployment. This is achieved through the use of Persistent Volume Claims (PVCs), which are requests by users for storage, specifying size, access modes, and other parameters.

#### Key Components

* **Persistent Volumes (PVs)**: A storage resource in a Kubernetes cluster that exists independently of any individual Pod.
* **Persistent Volume Claims (PVCs)**: A request by a user for storage, specifying size, access modes, and other parameters.
* **Storage Classes**: Define different classes of storage, allowing for dynamic provisioning of PVs with varying performance and availability characteristics.

### Access Modes

PVs support different access modes, which define how the volume can be accessed across the cluster. The following are the supported access modes:

1. **ReadWriteOnce (RWO)**: Mounted as read-write by a single node.
2. **ReadOnlyMany (ROX)**: Mounted as read-only by multiple nodes.
3. **ReadWriteMany (RWX)**: Mounted as read-write by multiple nodes.

### Storage Classes

StorageClasses in Kubernetes define different classes of storage, allowing for dynamic provisioning of PVs with varying performance and availability characteristics. This enables administrators to offer multiple storage options to users.

#### Example StorageClass YAML
```yml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: slow
provisioner: kubernetes.io/no-provisioner
volumeBindingMode: Immediate
allowedTopologies:
- matchLabelExpressions:
  - key: kubernetes.io/hostname
    values:
    - node1
  - key: kubernetes.io/hostname
    values:
    - node2
```

### Dynamic vs. Static Provisioning

PVs can be statically provisioned by administrators or dynamically provisioned based on StorageClasses when a PVC is created, providing flexibility in how storage is allocated.

#### Example PVC YAML
```yml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myclaim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 8Gi
```

### Lifecycle Management

The lifecycle of a PV is independent of any Pod that uses the PV. This means that data stored in a PV can outlive the Pods that access it, ensuring data persistence across Pod restarts and rescheduling.

### Reclaim Policy

PVs have a reclaim policy that determines what happens to the underlying storage resource after the PVC is released. Common policies include:

1. **Retain**: Keeps the data intact for manual reclamation.
2. **Recycle**: Performs a basic scrub (e.g., `rm -rf /thevolume/*`).
3. **Delete**: Deletes the storage resource, such as an AWS EBS volume.

#### Example Reclaim Policy YAML
```yml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mypv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
```

### Binding Process

When a PVC is created, Kubernetes matches it to a suitable PV based on the requested storage size and access modes. Once bound, the PV is exclusively associated with that PVC, ensuring consistent and reliable storage for the requesting Pod.

Key Points and Takeaways
------------------------

* **Decoupling Storage and Pods**: PVs decouple storage provisioning from Pod management.
* **Access Modes**: PVs support different access modes (RWO, ROX, RWX).
* **Storage Classes**: Define different classes of storage for dynamic provisioning.
* **Dynamic vs. Static Provisioning**: PVs can be provisioned statically or dynamically.
* **Lifecycle Management**: The lifecycle of a PV is independent of any Pod that uses it.
* **Reclaim Policy**: Determines what happens to the underlying storage resource after PVC release.

References
------------

* [Kubernetes Documentation: Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
* [Kubernetes Documentation: Storage Classes](https://kubernetes.io/docs/concepts/storage/storage-classes/)

## Key Takeaways

- To be updated.

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1880285956001132998)