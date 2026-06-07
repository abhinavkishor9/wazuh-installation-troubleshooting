# Wazuh Installation Notes

## Overview

This document summarizes my attempt to deploy the **Wazuh SIEM platform** in a Linux lab environment. The objective was to gain hands-on experience with SIEM deployment, Linux administration, and troubleshooting enterprise security software.

---

## Lab Environment

| Component | Details |
| ---------- | ---------------- |
| Operating System | Ubuntu Server |
| SIEM Platform | Wazuh |
| Components Installed | Wazuh Manager, Wazuh Indexer, Wazuh Dashboard |
| Shell | Bash |
| Service Manager | systemd |

---

# Installation Process

## Step 1: Update System Packages

Before installing Wazuh, the operating system packages were updated.

```bash
sudo apt update
sudo apt upgrade
```

---

## Step 2: Install Wazuh Components

The following components were installed:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

The installation completed successfully.

---

## Step 3: Verify Services

The status of each service was verified using:

```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

### Status

- ✅ Wazuh Manager running
- ✅ Wazuh Indexer running
- ⚠️ Wazuh Dashboard failed to start properly

---

## Step 4: Verify Listening Ports

To confirm that services were listening on the expected ports:

```bash
sudo lsof -i -P -n
```

Alternative command:

```bash
sudo netstat -tulpn
```

---

## Step 5: Test Local Connectivity

The Wazuh Indexer was tested using:

```bash
curl localhost:9200
```

This confirmed that the Indexer service was responding locally.

---

## Step 6: Review Configuration

The Dashboard configuration file was reviewed:

```
/etc/wazuh-dashboard/opensearch_dashboards.yml
```

The following settings were checked:

- server.host
- server.port
- opensearch.hosts

---

## Step 7: Review Logs

Dashboard logs were inspected using:

```bash
sudo journalctl -u wazuh-dashboard
```

Additional system logs:

```bash
sudo journalctl -xe
```

---

# Troubleshooting Activities

The following troubleshooting methodology was performed:

- Verified service status
- Checked running processes
- Verified listening ports
- Tested localhost connectivity
- Reviewed configuration files
- Examined service logs
- Validated service dependencies
- Investigated Dashboard startup failures

---

# Commands Used

```bash
systemctl
journalctl
curl
grep
lsof
netstat
cat
ls
```

---

# Skills Demonstrated

- Linux Administration
- Wazuh SIEM Deployment
- OpenSearch Connectivity
- Service Management
- Log Analysis
- Configuration Validation
- Network Troubleshooting
- Bash Command Line

---

# Lessons Learned

This lab provided practical exposure to deploying an enterprise SIEM platform and reinforced the importance of systematic troubleshooting.

Key learnings include:

- Understanding Wazuh Manager, Indexer, and Dashboard architecture
- Managing Linux services with `systemctl`
- Testing connectivity using `curl`
- Validating listening ports with `lsof` and `netstat`
- Reading logs with `journalctl`
- Following a structured troubleshooting methodology

Although the Dashboard service was not fully operational during this deployment, the troubleshooting process significantly improved my understanding of Linux administration and SIEM deployment.

---

# Next Steps

- Complete Dashboard deployment
- Integrate Windows endpoints
- Forward Windows Event Logs
- Configure custom detection rules
- Generate security alerts
- Perform SOC investigation scenarios
