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

<img width="950" height="506" alt="image" src="https://github.com/user-attachments/assets/15398468-d7b3-4718-ba71-2ac4ff3f2a40" />


- Metrics showing up

<img width="677" height="266" alt="image" src="https://github.com/user-attachments/assets/f04f0f3c-d259-4e2e-9d68-878bd8056b69" />

-Rolldice telemetry

![alt text](image-2.png)


