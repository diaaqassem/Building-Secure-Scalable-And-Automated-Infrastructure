
---

# Kubeadm Microservices Project Deployment

## Project Overview

This project demonstrates deploying a complete microservices-based application on a Kubernetes cluster set up using **Kubeadm**. The cluster consists of:

* 1 Master node (VM on cloud)
* 1 Worker node (VM on cloud)

The project includes multiple applications, monitoring, persistent storage, and secure network configurations.

---

## Cluster Setup

* **Kubernetes Setup**: Installed using [Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)
* **Nodes**:

  * **Master Node**: Cloud VM
  * **Worker Node**: Cloud VM

---

## Applications & Components

### 1. Backend Microservice

* **Deployment**: `2 replicas`
* **Horizontal Pod Autoscaler (HPA)**: min `2` pods, max `5` pods
* **Service**: `ClusterIP`
* **ConfigMap**: Used for environment variables
* **NetworkPolicy**: Defined to control communication with Frontend & DB

### 2. Database (DB)

* **Deployment**: `2 replicas`
* **PersistentVolume (PV)\` and PersistentVolumeClaim (PVC)**: for data persistence
* **Service**: `ClusterIP`
* **NetworkPolicy**: Restricted access from Backend only

### 3. Frontend Application

* **Deployment**: `2 replicas`
* **HPA**: min `2` pods, max `5` pods
* **Service**: `NodePort`
* **NetworkPolicy**: Can only access Backend

### 4. XO Game Application

* **Deployment**: `2 replicas`
* **Service**: `NodePort`

### 5. CRUD Application

* **Deployment**: `2 replicas`
* **Service**: `NodePort`

---

## Monitoring

* **Prometheus**: for collecting metrics
* **Grafana**: for dashboards and visualization

---

## Networking & Security

* **NetworkPolicy**: Implemented to control traffic between services:

  * Backend ↔️ Frontend
  * Backend ↔️ DB
  * Isolation of sensitive components

---

## How to Deploy

### Prerequisites

* Kubernetes cluster (created with kubeadm)
* kubectl configured for the cluster
* Helm (for installing Prometheus & Grafana)

### Steps

1. **Create ConfigMaps**

   ```bash
   kubectl apply -f env-secret.yml
   ```

2. **Deploy Backend**

   ```bash
   kubectl apply -f app-deployment..yaml
   kubectl apply -f hpa.yaml
   kubectl apply -f clusterip-svc-backend.yml
   ```

3. **Deploy Database**

   ```bash
   kubectl apply -f persistent-volume.yaml
   kubectl apply -f persistent-volume-claim.yaml
   kubectl apply -f storage-class.yaml
   kubectl apply -f mongodb-deployment.yaml
   kubectl apply -f db-svc-clusterip.yaml
   ```

4. **Deploy Frontend**

   ```bash
   kubectl apply -f react-app-deployment.yml
   kubectl apply -f nodeport-react-app-svc.yml
   ```

5. **Deploy XO Game App**

   ```bash
   kubectl apply -f xo-app-deployment.yml
   kubectl apply -f NodePort-svc.yml
   ```

6. **Deploy CRUD App**

   ```bash
   kubectl apply -f crud-app-deployment.yml
   kubectl apply -f NodePort-svc.yml
   ```

7. **Install Prometheus & Grafana**

   ```bash
     Check pdf Setup Giude 
   ```

---

## Accessing Services

| Application | Access Method                           |
| ----------- | --------------------------------------- |
| Frontend    | NodePort                                |
| XO Game     | NodePort                                |
| CRUD App    | NodePort                                |
| Backend     | ClusterIP                               |
| DB          | ClusterIP                               |
| Grafana     | NodePort / LoadBalancer (as configured) |

---

## References

* [Kubeadm Official Docs](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)
* [Kubernetes NetworkPolicy](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
* [Helm](https://helm.sh/)
* [Prometheus](https://prometheus.io/)
* [Grafana](https://grafana.com/)
