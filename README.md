# K8S SigNoz Infra Monitoring


## 🛠 Setup Instructions

### Prerequisites

- Kubernetes cluster (tested on vSphere)
- Helm installed
- Ansible installed
- SigNoz running on Docker (collector reachable via host IP)

### 🔼 To Deploy Agent

```bash
ansible-playbook ansible/up.yaml
```

### 🔽 To Uninstall Agent

```bash
ansible-playbook ansible/down.yaml
```

## 📦 What’s Included

- `up.yaml` and `down.yaml`: Ansible playbooks
- `values.yaml`: Helm chart override for OTEL collector IP/port
- `screenshots/`


## 📸 Screenshots

- SigNoz hosts

![alt text](image-1.png)

- Metrics showing up

![alt text](image-2.png)


