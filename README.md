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

## 𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚁𝙴𝚂𝙾𝚄𝚁𝙲𝙴 𝙶𝚁𝙾𝚄𝙿

### Step 1: Go to `portal.azure.com` and search for `Resource Groups`

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/e879227c-64d5-4437-8d15-4df415684957" />

### Step 2: `+ Create` a Resource Group

```
Basics

Resource Group
  └─ Subscription: Azure Subscription 1  
  └─ Resource Group Name: RG-willis 
  └─ Region: (US) East US 2
Review + Create
  └─ Create (When Prompted)
```

---

## 𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚅𝙸𝚁𝚃𝚄𝙰𝙻 𝙽𝙴𝚃𝚆𝙾𝚁𝙺

### Step 1: In Azure Portal, search for `Virtual Network` 

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/3ad66e12-4e04-4654-b7cf-7f832f85da22" />

### Step 2: `+ Create` Virtual Network

```
Basics

Project Details
  └─ Subscription: Azure Subscription 1  
  └─ Resource Group Name: RG-willis 
Instance Details
  └─ Virtual Network Name: vnet-willis
  └─ Region: (US) East US 2
Review + Create
  └─ Create (When Prompted)
```

---

## 𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚅𝙸𝚁𝚃𝚄𝙰𝙻 𝙼𝙰𝙲𝙷𝙸𝙽𝙴

### Step 1: In Azure Portal, search for `Virtual Machines`

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/1b5184f5-0b63-47e0-bb00-bad092289d57" />

### Step 2: `+ Create` a new `virtual machine`

<img width="433" height="599" alt="Extra 2" src="https://github.com/user-attachments/assets/f3e8dc4d-470a-4d60-9012-ee34b574ed68" />

### Step 3: My `Virtual Machine` settings

```
Basics

Project Details
  └─ Subscription: Azure Subscription 1  
  └─ Resource Group: RG-willis
Instance Details 
  └─ Virtual Machine Name: CORP-NET-EAST  
  └─ Region: (US) East US 2
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

```
Review + Create
  └─ Create (When Prompted)
```

---

## 🍯 𝙲𝚁𝙴𝙰𝚃𝙴 𝚃𝙷𝙴 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃

### Step 1: Go to the `Network Security Group` inside your `Virtual Machine`

```
YourVirtualMachine
└─ Networking
  └─ Network Settings
```

---

### Step 2: Delete the `RDP` `Inbound Security Rule`
  
<img width="2196" height="402" alt="Lab 23" src="https://github.com/user-attachments/assets/7dd7b6d6-ca5d-487c-a7c0-4608d753a10a" />

---

### Step 3: `+ Add` a new `Inbound Security Rule`

```
Add Inbound Security Rule
  └─ Source: Any
  └─ Source Port Ranges: *
  └─ Destination: *
  └─ Service: Custom
  └─ Destination Port Ranges: *
  └─ Protocol: Any
  └─ Action: Allow
  └─ Priority: 300
  └─ Name: DANGER_AllowAnyCustomAnyInbound
```

---

### Step 4: Log into your `Virtual Machine` with `Remote Desktop Connection`

```
YourVirtualMachine
└─ Overview
  └─ Public IP Address
```

<img width="405" height="248" alt="Extra 5" src="https://github.com/user-attachments/assets/747f1402-0f15-4f73-ace8-cfc2f558e4d7" /></br>

***Note:** You will need the **username** and **password** you used to create your Virtual Machine to log in.*

---

### Step 5: Turn off the Windows Defender Firewall

```
Win + R
  └─ wf.msc
```

<img width="1041" height="779" alt="Lab 28" src="https://github.com/user-attachments/assets/0562dc50-79da-4c5e-b018-1fff70469493" />

---

## 𝚅𝙰𝙻𝙸𝙳𝙰𝚃𝙴 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃 𝙴𝚇𝙿𝙾𝚂𝚄𝚁𝙴

### Step 1: From your `Local Machine`, ping your `Virtual Machine's` Public IP Address

<img width="452" height="246" alt="Lab 29" src="https://github.com/user-attachments/assets/f560ce9c-ef11-4274-9da2-2424a312c787" />

### Step 2: Simulate `Brute-Force` Attempts

- ### Log out of your `Virtual Machine` and log back in with the incorrect username and password

<img width="451" height="414" alt="Lab 30" src="https://github.com/user-attachments/assets/810de6dd-94ff-41ce-9b70-9f0623a5486e" />

- ### Log back into your `Virtual Machine` and check `Event Viewer`

```
Win + R
└─ eventvwr.msc
  └─ Windows Logs
    └─ Security
```

<img width="907" height="381" alt="Lab 31" src="https://github.com/user-attachments/assets/c7d293e9-db4b-4623-8bb1-454948581740" /></br>

***Note:** EventID `4625` is a failed logon attempt. We can investigate further and see that a user named `employee` tried to log into our Virtual Machine. The honeypot is live!*

---

## 𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝙻𝙾𝙶 𝙰𝙽𝙰𝙻𝚈𝚃𝙸𝙲𝚂 𝚆𝙾𝚁𝙺𝚂𝙿𝙰𝙲𝙴

### Step 1: In Azure Portal, search for `Log Analytics Workspaces` 

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/90014f16-a3ad-4234-b7d7-5ebcca19d05a" />

### Step 2: `+ Create` a new `Log Analytics Workspace`

```
Basics

Project Details
  └─ Subscription: Azure Subscription 1  
  └─ Resource Group: RG-willis
Instance Details 
  └─ Name: LAW-Willis  
  └─ Region: (US) East US 2
Review + Create
  └─ Create (When Prompted)
```

---

## 𝙰𝙲𝚃𝙸𝚅𝙰𝚃𝙴 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻

### Step 1: In Azure Portal, search for `Microsoft Sentinel` 

<img width="626" height="279" alt="Extra 1" src="https://github.com/user-attachments/assets/0ff5da10-d4bc-499c-b1d2-f903af0417a4" />

### Step 2: Select Your `Log Analytics Workspace` and `Add`

<img width="1173" height="124" alt="Lab 7" src="https://github.com/user-attachments/assets/e41d901e-57a8-4bfa-8406-a226fb2f9faa" />

### Step 3: In Microsoft Sentinel, Install Windows Security Events  

```
Content Management
  └─ Content Hub  
Search: Security Event
  └─ ☑ Windows Security Events
    └─ Install
```




































