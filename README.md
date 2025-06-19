# ex-yaml-k8b-airflow
Deploy Docker Airflow in Kubernetes

## About
This project provides a minimal example of deploying Apache Airflow using the puckel/docker-airflow image on a local Kubernetes cluster with Minikube. It includes:
- Namespace and PersistentVolumeClaims for Airflow logs, DAGs, and Postgres data
- Deployments and Services for Postgres and Airflow
- Step-by-step instructions for setup, access, and cleanup

## Quick Start

### 1. Start Minikube with CPU and Memory Limits
```sh
minikube start --cpus=2 --memory=4096mb
```

### 2. Apply the Kubernetes YAML
```sh
kubectl apply -f ex-yaml-k8b-airflow.yaml
```

### 3. Expose the Airflow Webserver Service
```sh
minikube service airflow-web -n airflow
```
This will open the Airflow UI in your browser. To get the URL only:
```sh
minikube service airflow-web -n airflow --url
```

### 4. Clean Up (Delete All Resources)
```sh
kubectl delete -f ex-yaml-k8b-airflow.yaml
```

---

- Make sure you have [Minikube](https://minikube.sigs.k8s.io/) and [kubectl](https://kubernetes.io/docs/tasks/tools/) installed.
- All resources are created in the `airflow` namespace.
