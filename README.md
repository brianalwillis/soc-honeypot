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

## 𝚂𝙴𝚃𝚄𝙿 𝙰𝚉𝚄𝚁𝙴 𝚂𝚄𝙱𝚂𝙲𝚁𝙸𝙿𝚃𝙸𝙾𝙽

### Step 1: Create a free Azure subscription: [`https://azure.microsoft.com`](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)

<img width="1594" height="677" alt="Lab 1" src="https://github.com/user-attachments/assets/943202f4-4ee4-4bdc-817c-5071ae21f0e5" /></br>

<img width="1314" height="488" alt="Lab 2" src="https://github.com/user-attachments/assets/e2857ac0-8dcd-4699-b139-2181c4e4859d" /></br>

*Note: You will have to sign up and provide valid payment information, but you will **NOT** be charged.*

### Step 2: After your subscription is created, you can log in at: [`https://portal.azure.com`](https://portal.azure.com)

---

## 𝙲𝚁𝙴𝙰𝚃𝙴 𝚃𝙷𝙴 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃

### Step 1: Go to `portal.azure.com` and search for `virtual machines`

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/1b5184f5-0b63-47e0-bb00-bad092289d57" />

### Step 2: `+Create` a new `virtual machine`

<img width="433" height="599" alt="Extra 2" src="https://github.com/user-attachments/assets/f3e8dc4d-470a-4d60-9012-ee34b574ed68" />

### Step 3: My `virtual machine` settings

```
Basics

Project Details
└─ Subscription: Azure Subscription 1  
  └─ Resource Group: Create New
Instance Details 
└─ Virtual Machine Name: CORP-NET-EAST  
└─ Region: (US) East US
└─ Image: Windows 10 Pro, Version 22H2 - x64 Gen2  
Size
└─ Standard_B1s 1 vCPU, 1 GiB RAM  
Administrator Account
└─ Username: YourUsername
└─ Password: YourPassword
└─ Confirm Password: YourPassword  
Licensing  
└─ ☑ I confirm I have an eligible Windows 10/11 license
```

```
Disks

OS Disk
└─ OS Disk Type: Standard HDD 
```

```
Networking

Network Interface
└─ Virtual Network: Create New 
└─ Subnet: Default 
└─ Public IP: (new)  
└─ NIC Network Security Group: Basic
└─ ☑ Delete public IP and NIC when VM is deleted 
```

```
Monitoring

Diagnostics
└─ Boot Diagnostics: Disable 
```

### Step 4: Review + Create → Create (When Prompted)

---





















