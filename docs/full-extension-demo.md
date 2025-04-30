# 🛡️ Zero Trust Network Architecture Overview

This document outlines key components of a Zero Trust network design using Markdown extensions to enhance readability and interactivity.

---

## 🔐 Identity & Access Management (IAM)

!!! tip "Use Role-Based Access Control (RBAC)"
    RBAC helps minimize over-permissioning and aligns with the principle of least privilege.

=== "AWS Example"

    ```yaml
    Statement:
      - Effect: Allow
        Action: ec2:DescribeInstances
        Resource: "*"
    ```

=== "Azure Example"

    ```json
    {
      "RoleDefinitionName": "Reader",
      "Actions": [ "Microsoft.Compute/virtualMachines/read" ]
    }
    ```

---

## 🌐 Network Segmentation

```bash
# Firewall rule to allow SSH from a bastion host
iptables -A INPUT -s 10.0.0.5 -p tcp --dport 22 -j ACCEPT
```

!!! warning "Avoid opening SSH to the public internet"
    Exposing port 22 to `0.0.0.0/0` introduces serious risk. Always scope access narrowly.

??? example "Show example NGINX configuration"

    ```nginx
    server {
        listen 443 ssl;
        ssl_certificate /etc/nginx/cert.pem;
        ssl_certificate_key /etc/nginx/key.pem;
    }
    ```

---

## 🧭 Monitoring & Logging

- Centralized logs
- Alerts for unauthorized access
- SIEM integration (e.g., Splunk, Sentinel)

```bash
# Example: send logs to remote syslog
logger -n 10.1.1.10 -P 514 "Unauthorized login attempt"
```

!!! note
    Logs should be immutable and retained according to compliance requirements.

---

## ✅ Summary

- Use tabs to document platform-specific commands
- Collapse long configs using details blocks
- Warn against risky setups with admonitions
- Highlight best practices and standards
