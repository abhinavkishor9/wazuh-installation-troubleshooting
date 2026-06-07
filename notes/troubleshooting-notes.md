# Wazuh Troubleshooting Notes

## Overview

This document outlines the troubleshooting process followed during the deployment of the **Wazuh SIEM platform** in a Linux lab environment.

The primary issue encountered was that the **Wazuh Dashboard service failed to start**, while the **Wazuh Manager** and **Wazuh Indexer** services were running successfully.

The objective of this exercise was to diagnose the problem using a structured troubleshooting methodology and improve understanding of Wazuh architecture and Linux service management.

---

# Problem Statement

After completing the installation:

| Component | Status |
|------------|------------|
| Wazuh Manager | ✅ Running |
| Wazuh Indexer | ✅ Running |
| Wazuh Dashboard | ⚠️ Failed to Start |

The Dashboard service could not be accessed through the web interface, requiring further investigation.

---

# Troubleshooting Steps

## 1. Verify Service Status

Verified that all Wazuh services were installed and checked their status.

```bash
sudo systemctl status wazuh-manager
sudo systemctl status wazuh-indexer
sudo systemctl status wazuh-dashboard
```

Result:

- Manager running successfully
- Indexer running successfully
- Dashboard service failed to start

---

## 2. Review Dashboard Logs

Checked the Dashboard logs to identify startup errors.

```bash
sudo journalctl -u wazuh-dashboard
```

Additional logs:

```bash
sudo journalctl -xe
```

This provided useful information about service initialization and configuration issues.

---

## 3. Verify Listening Ports

Checked whether the expected ports were open and listening.

```bash
sudo lsof -i -P -n
```

Alternative command:

```bash
sudo netstat -tulpn
```

This confirmed which services were actively accepting connections.

---

## 4. Test Indexer Connectivity

Verified that the Wazuh Indexer was responding locally.

```bash
curl localhost:9200
```

The successful response confirmed that the backend Indexer service was operational.

---

## 5. Review Configuration Files

Inspected the Dashboard configuration file:

```
/etc/wazuh-dashboard/opensearch_dashboards.yml
```

Reviewed parameters including:

- server.host
- server.port
- opensearch.hosts

---

## 6. Validate Service Dependencies

Confirmed that backend services were running before troubleshooting the Dashboard.

```bash
sudo systemctl status wazuh-indexer
```

This verified that the Dashboard dependency was available.

---

# Commands Used

```bash
systemctl
journalctl
curl
lsof
netstat
grep
cat
ls
```

---

# Skills Demonstrated

- Linux Administration
- SIEM Deployment
- Wazuh Architecture
- OpenSearch Connectivity
- Service Management
- Log Analysis
- Configuration Validation
- Network Troubleshooting
- Structured Debugging

---

# Lessons Learned

This troubleshooting exercise reinforced several important concepts:

- Verify service status before modifying configurations.
- Review logs to identify root causes instead of guessing.
- Validate backend connectivity before troubleshooting frontend services.
- Confirm required ports are listening.
- Follow a structured troubleshooting methodology to isolate issues efficiently.

Although the Dashboard service was not fully operational during this deployment, the troubleshooting process provided valuable practical experience with Linux system administration and enterprise SIEM deployment.

---

# Future Improvements

- Complete Dashboard deployment
- Resolve Dashboard startup issues
- Integrate Windows endpoints
- Forward endpoint logs to Wazuh
- Generate security alerts
- Build SOC investigation scenarios using collected telemetry
