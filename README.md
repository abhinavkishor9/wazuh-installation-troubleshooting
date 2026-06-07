# Wazuh SIEM Deployment Lab

## Overview

This project documents my attempt to deploy the Wazuh SIEM platform in a Linux lab environment.

The objective was to gain hands-on experience with SIEM deployment, Linux administration, service management, and troubleshooting while preparing for SOC Analyst roles.

Although the deployment encountered issues with the Wazuh Dashboard service, the troubleshooting process provided valuable insights into Wazuh architecture and system administration.

---

# Lab Environment

- Ubuntu Server
- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- OpenSearch
- systemd
- Linux CLI

---

# Objectives

- Install Wazuh SIEM
- Configure Manager
- Configure Indexer
- Deploy Dashboard
- Verify service communication
- Validate ports and connectivity
- Troubleshoot startup failures

---

# Installation Progress

| Component | Status |
|------------|------------|
| Wazuh Manager | ✅ Installed |
| Wazuh Indexer | ✅ Installed |
| Wazuh Dashboard | ⚠️ Startup issue encountered |
| OpenSearch Connectivity | Tested |
| Linux Services | Verified |
| Port Verification | Completed |

---

# Troubleshooting Performed

The following troubleshooting steps were completed:

- Verified service status using systemctl
- Checked running processes
- Verified listening ports
- Examined dashboard configuration files
- Tested localhost connectivity
- Reviewed service dependencies
- Checked Indexer availability
- Investigated Dashboard startup failures

Commands used included:

```
systemctl status
journalctl
lsof
netstat
curl
grep
```

---

# Lessons Learned

This lab improved my understanding of:

- SIEM architecture
- Wazuh components
- OpenSearch communication
- Linux service management
- Port troubleshooting
- Log analysis
- Configuration validation
- System administration

---

# Skills Demonstrated

- Linux
- Bash
- SIEM
- Wazuh
- OpenSearch
- Troubleshooting
- Incident Analysis
- Service Management
- Log Investigation

---

# Future Improvements

- Complete Dashboard deployment
- Integrate Windows endpoint
- Forward logs to Wazuh
- Create custom detection rules
- Generate alerts
- Build SOC investigation scenarios

---
