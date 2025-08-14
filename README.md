## K8S Infra Helm Chart with Ansible for SigNoz on TrueNAS
## 1. Project Overview
## This project deploys the K8S Infra Helm chart on a Kubernetes cluster using Ansible playbooks (up.yaml and down.yaml) to send logs and telemetry to a SigNoz installation running in Docker on TrueNAS. The setup allows overriding Helm values to specify an upstream OpenTelemetry (otel) collector. Additionally, the rolldice sample application is deployed to verify telemetry flow to SigNoz.
## 2. Prerequisites
- Kubernetes cluster (tested on vSphere environment)
- Ansible installed on control machine
- Helm installed on control machine
- SigNoz running in Docker on TrueNAS
- Access to upstream Otel collector URL
- Git installed
## 3. Repository Structure
```
k8s-infra-ansible/
├─ playbooks/
│  ├─ up.yaml         # Ansible playbook to install K8S Infra Helm chart
│  ├─ down.yaml       # Ansible playbook to uninstall K8S Infra Helm chart
├─ values/
│  ├─ k8s-infra-values.yaml  # Custom Helm values (otel collector override)
│  ├─ rolldice-values.yaml   # Helm values for rolldice app
├─ inventory/
│  └─ hosts.ini       # Ansible inventory with Kubernetes control node
└─ README.md
```
## 4. Installation Instructions
Run the Ansible playbook to install the K8S Infra Helm chart:
```bash
ansible-playbook -i inventory/hosts.ini playbooks/up.yaml
```
## 5. Removal Instructions
Run the Ansible playbook to uninstall the K8S Infra Helm chart:
```bash
ansible-playbook -i inventory/hosts.ini playbooks/down.yaml
```
## 6. Overriding Helm Values for Upstream Otel Collector
Modify `values/k8s-infra-values.yaml` to set the upstream Otel collector endpoint:
```yaml
otelCollectorEndpoint: "otel-collector.truenas.local:4317"
```
## 7. Testing on vSphere
The deployment was tested on a vSphere-based Kubernetes cluster. After running the `up.yaml` playbook, Helm confirmed successful installation and logs were visible in the SigNoz dashboard.
## 8. Adding Rolldice App and Verifying Telemetry
Deploy the rolldice sample application:
```bash
helm install rolldice ./rolldice-chart -f values/rolldice-values.yaml
```
Generate test requests:
```bash
kubectl exec -it <rolldice-pod> -- curl http://localhost:8080/roll
```
Verify that traces and logs from rolldice appear in the SigNoz UI.
## 9. Expected Output & Verification
- Helm release `k8s-infra` shows status `deployed`
- SigNoz dashboard displays Kubernetes metrics and logs
- Rolldice application telemetry visible in SigNoz traces
