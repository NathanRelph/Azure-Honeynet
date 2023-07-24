# Building a SOC + Honeynet in Azure (Live Traffic)
![SOC_Honeynet_Map](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/145f5f20-ae14-4f1f-9185-22bf2bab1857)


## Introduction

Text Here

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![Before_Hardening](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/abc3757c-b8d0-475b-b3f4-30cbcfd86e4f)


## Architecture After Hardening / Security Controls
![After_Hardening](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/b11e5282-5167-4655-94db-62e706978cd0)


The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

## Attack Maps Before Hardening / Security Controls
![(before)nsg-malicious-allowed-in](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/e8fcb175-eb9a-4a27-8f79-4cfe60a92683)
![(before)windows-rdp-smb-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/bf5cb7de-3681-4eeb-afac-afefbb483ae6)
![(before)mssql-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/e97d22b1-78cc-4c53-b0d7-31b2ea00bb47)
![(before)syslog-ssh-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/30b92af3-03e1-474d-9aba-070fd1163713)


## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
- Start Time: 7/20/2023, 7:18:30 PM
- Stop Time: 7/21/2023, 7:18:30 PM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 21129
| Syslog                   | 2005
| SecurityAlert            | 1
| SecurityIncident         | 243
| AzureNetworkAnalytics_CL | 1714

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
- Start Time: 7/22/2023, 5:32:05 PM 
- Stop Time: 7/23/2023, 5:32:05 PM

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 9162
| Syslog                   | 2
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

## Conclusion

Text here.

Text here.
