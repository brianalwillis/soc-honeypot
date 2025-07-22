<h1 = align=center>𝙸𝙼𝙿𝙻𝙴𝙼𝙴𝙽𝚃𝙸𝙽𝙶 𝙰 𝚂𝙴𝙲𝚄𝚁𝙸𝚃𝚈 𝙾𝙿𝙴𝚁𝙰𝚃𝙸𝙾𝙽 𝙲𝙴𝙽𝚃𝙴𝚁 (𝚂𝙾𝙲)
  
  𝙰𝙽𝙳 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝙰𝚉𝚄𝚁𝙴</h1>

<p = align=center>
<img width="1548" height="748" alt="SOC Final drawio (1)" src="https://github.com/user-attachments/assets/aadd2f1a-4ab0-4cac-8c85-c942e5c91702" />
</p>

## 🛠️ 𝚃𝙴𝙲𝙷𝙽𝙾𝙻𝙾𝙶𝚈 & 𝙿𝙻𝙰𝚃𝙵𝙾𝚁𝙼𝚂 𝚄𝚃𝙸𝙻𝙸𝚉𝙴𝙳

- `Microsoft Azure:`</br>
  Core cloud platform used to build and host the SOC and honeypot infrastructure.

- `Windows 10 VM:`</br>
  Deployed as a honeypot to attract and monitor unauthorized access attempts.

- `Network Security Group (NSG) / Firewall:`</br>
  Intentionally configured to allow all inbound traffic to maximize visibility and expose the honeypot VM to real-world attack attempts.

- `Log Analytics Workspace:`</br>
  Centralized log collection hub for ingesting and analyzing event data from the VM and Sentinel.

- `Microsoft Sentinel:`</br>
  Cloud-native SIEM solution used to detect, investigate, and respond to threats in real time.

- `Kusto Query Language (KQL):`</br>
  Used to write custom detection rules, analyze login attempts, and visualize attacker behavior in Sentinel dashboards.

  ---

## 🎯 𝙾𝙱𝙹𝙴𝙲𝚃𝙸𝚅𝙴

The objective of this project was to design and implement a simulated `Security Operations Center` (SOC) environment in `Microsoft Azure`, centered around a `Windows 10` virtual machine acting as a `honeypot`. The goal was to attract and analyze real-world unauthorized access attempts by exposing the VM to public traffic. Using tools such as `Microsoft Sentinel`, `Log Analytics Workspace`, and `Kusto Query Language` (KQL), I monitored, detected, and investigated threat activity. This project demonstrates core SOC capabilities, including threat detection, alerting, incident response, and visualization through workbooks.

---

## SETUP AZURE SUBSCRIPTION

### Step 1: Create a free Azure subscription: [`https://azure.microsoft.com`](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)

