# Production API Latency Incident

## Overview

Production API latency alerts were triggered in Sysdig for customer-facing payment services hosted in AWS EKS.

The issue caused intermittent response delays and elevated application response times exceeding SLA thresholds.

---

# Environment

- Environment: Production
- Cloud Provider: AWS
- Kubernetes Platform: EKS
- Monitoring Stack: Sysdig + CloudWatch
- Severity: SEV-2

---

# Detection

## Sysdig Alerts

- API latency exceeded 3 seconds
- Increased HTTP 5xx errors
- Elevated CPU utilization
- Network throughput anomalies

---

# Investigation

Engineering teams performed:

```bash
kubectl top pods

kubectl describe nodes

kubectl logs

kubectl get hpa
```

---

# Findings

Root cause identified:

- CPU throttling during peak traffic
- Insufficient pod autoscaling thresholds
- Delayed horizontal pod autoscaler reaction times

---

# Remediation

Actions taken:

- Increased CPU requests
- Tuned HPA scaling policies
- Added additional worker nodes
- Restarted affected deployments

---

# Operational Improvements

- AI-based anomaly detection
- Enhanced synthetic monitoring
- Improved autoscaling policies
- Production traffic simulation testing

---

# Outcome

Latency stabilized within SLA thresholds following remediation activities.
