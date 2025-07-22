# 🚀 GitOps CD Repository - `gitops-devops`

This is the **Continuous Delivery (CD)** GitOps repository for deploying a 3-tier Node.js application using **Helm** and **Argo CD** on Kubernetes.

---

## 📦 Purpose

This repository manages only the **Kubernetes Helm charts** and **Argo CD Application YAMLs** required for:

- Frontend (React-based UI)
- Backend (Node.js Express API)
- MySQL (Database layer)

This repo does **not** contain application code — it's for **deployment only**, following the GitOps model.

---


---

## 🔄 GitOps Flow (Using Argo CD)

> Argo CD watches this repo and syncs changes to the cluster.

1. Jenkins (CI pipeline) builds Docker images and pushes to DockerHub.
2. You **manually update** the image tag and color (`blue` or `green`) in this repo's `values.yaml`.
3. Argo CD detects the change and deploys it to the cluster automatically.

---

## 🟢🔵 Blue/Green Deployment (Frontend)

We use **Blue/Green Deployment** for safer rollouts and quick rollback:

- `frontend-app.yaml` → Blue deployment
- `frontend-green-app.yaml` → Green deployment

You can switch traffic by changing this value in `values.yaml`:

```yaml
deploymentColor: green  # or "blue"
