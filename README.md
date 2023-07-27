# Building a SOC + Honeynet in Azure (Live Traffic)  
![SOC_Honeynet_Map](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/145f5f20-ae14-4f1f-9185-22bf2bab1857)


## Introduction
In this Azure lab, I learned to create a honeynet in the cloud using virtual machines and azure services like Sentinel and Defender for Cloud.  The goal in completing this lab was to create an eviornement in which attackers could get into my network, record their IPs and map them, and then harden the network again the finish off the project.



<h3><ins>Analyzed Metrics:</ins></h3>

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls
![Before_Hardening](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/abc3757c-b8d0-475b-b3f4-30cbcfd86e4f)
For the "BEFORE" metrics, all resources were originally deployed, exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet; aka, no use for Private Endpoints.

## Architecture After Hardening / Security Controls
![After_Hardening](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/b11e5282-5167-4655-94db-62e706978cd0)
For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint

<h3><ins>Architecture:</ins></h3>

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Active Directory/ Activity Logs
- Azure Key Vault
- Azure Storage Account

<h3><ins>Azure Services/Regulations:</ins></h3>

- Sentinel &#8594;
- Defender &#8594;
- NIST SP 800 53 R4 &#8594;
- PCI DSS 4 &#8594; 

## Hardening Approach

<kbd>![Screenshot 2023-07-23 193435](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/a67c0213-50e1-450b-9c03-1070c1f03ef8)</kbd>
- This screenshot displays

<kbd>![Screenshot 2023-07-23 193155](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/c4b5af56-e9d8-4218-a9e4-199064215be8)</kbd>
- This screenshot displays
  
<kbd>![Screenshot 2023-07-23 193131](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/c7827c4e-7100-434c-bcd5-a2341695d776)</kbd>
- This screenshot displays



## Attack Maps Before Hardening / Security Controls

- This attack map below displays the
<kbd>![(before)nsg-malicious-allowed-in](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/e8fcb175-eb9a-4a27-8f79-4cfe60a92683)</kbd>

- This attack map below displays the
<kbd>![(before)windows-rdp-smb-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/bf5cb7de-3681-4eeb-afac-afefbb483ae6)</kbd>

- This attack map below displays the
<kbd>![(before)mssql-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/e97d22b1-78cc-4c53-b0d7-31b2ea00bb47)</kbd>

- This attack map below displays the
<kbd>![(before)syslog-ssh-auth-fail](https://github.com/NathanRelph/Azure-Honeynet/assets/140288097/30b92af3-03e1-474d-9aba-070fd1163713)</kbd>




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
