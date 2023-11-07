# CYBERSECURITY-HONEYNET-AND-SOC-MANAGEMNT
# Building a SOC + Honeynet in Azure (Live Traffic)
![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/70b51ae1-ed8f-40dc-b2f2-a2bbf7bcaa83)


## Introduction

In this project, I created a mini honeynet within Microsoft Azure and collected log data from various sources, confoguring and linking it into a Log Analytics workspace. This data was subsequently leveraged by Microsoft Sentinel to create attack visualizations, initiate alerts, and generate incident reports. Over the course of this project, I conducted two sets of security metric assessments within an initially vulnerable environment: one over a 24-hour period, followed by the implementation of security measures to harden the environment, and another 24-hour assessment. then show the results below. The metrics we will show are"


- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)
- Result after Hardening.

## Architecture Before Hardening / Security Controls
![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/e81c6c0c-2417-4f98-94be-0ea21390ab0c)



## Architecture After Hardening / Security Controls
![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/24d5cd92-3e9b-43a5-bc9c-4b44a7ff72ee)


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
![Before Hardening Network-Sec-Group-Malicious-Allowed-in](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/94d2b52a-49df-4c4d-929d-6e6afcc0824e)<br>
![Before Hardening Linux-ssh-auth-fail](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/4066c2f1-428f-4344-9b88-bd76601b83e1)<br>
![After Hardening Windows-RDP_Auth-Failure](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/8a8caf98-8609-4843-bc98-146e4164c6bc)<br>
![Before Hardening MS-SQL-Auth-Fail](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/baf05324-28bf-4425-8c66-6187f38e7096)<br>


## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:


![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/dc40147a-2772-431d-a647-490d9f21ac5f)



	

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Attack Maps After Hardening / Security Controls

![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/cd25ab5f-55e8-4ec9-95af-432a973d7b1a)

![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/70ada3b1-d193-4e75-957d-51350739dad0)

![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/0eb64ccf-9dcb-4eb6-bb7b-55e9aa83ea66)

![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/d8e95d67-5676-4342-9dfe-5dfda1c63681)

		...Note: If you noticed the qury retured no result because the VMs have hardened, therefore there is no incident as of 24hrs ago.

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:

![image](https://github.com/MamusIbebe/MS-AZURE-HONEYNET-SOC-MANAGEMNT/assets/149246488/0ff5a054-8724-4d59-b794-b32fa6108ab4)


## Conclusion

In this project, a mini honeynet was constructed in Microsoft Azure and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was employed to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the insecure environment before security controls were applied, and then again after implementing security measures. It is noteworthy that the number of security events and incidents were drastically reduced after the security controls were applied, demonstrating their effectiveness.

It is worth noting that if the resources within the network were heavily utilized by regular users, it is likely that more security events and alerts may have been generated within the 24-hour period following the implementation of the security controls.
