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

## 𝚃𝙰𝙱𝙻𝙴 𝙾𝙵 𝙲𝙾𝙽𝚃𝙴𝙽𝚃𝚂

- [SETUP AZURE SUBSCRIPTION](#setup-azure-subscription)
- [𝚂𝙴𝚃𝚄𝙿 𝙰𝚉𝚄𝚁𝙴 𝚂𝚄𝙱𝚂𝙲𝚁𝙸𝙿𝚃𝙸𝙾𝙽](#setup-azure-subscription)
- [𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚁𝙴𝚂𝙾𝚄𝚁𝙲𝙴 𝙶𝚁𝙾𝚄𝙿](#create-a-resource-group)
- [𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚅𝙸𝚁𝚃𝚄𝙰𝙻 𝙽𝙴𝚃𝚆𝙾𝚁𝙺](#create-a-virtual-network)
- [𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝚅𝙸𝚁𝚃𝚄𝙰𝙻 𝙼𝙰𝙲𝙷𝙸𝙽𝙴](#create-a-virtual-machine)
- [𝙲𝚁𝙴𝙰𝚃𝙴 𝚃𝙷𝙴 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃](#create-the-honeypot)
- [𝚅𝙰𝙻𝙸𝙳𝙰𝚃𝙴 𝙷𝙾𝙽𝙴𝚈𝙿𝙾𝚃 𝙴𝚇𝙿𝙾𝚂𝚄𝚁𝙴](#validate-honeypot-exposure)
- [𝙲𝚁𝙴𝙰𝚃𝙴 𝙰 𝙻𝙾𝙶 𝙰𝙽𝙰𝙻𝚈𝚃𝙸𝙲𝚂 𝚆𝙾𝚁𝙺𝚂𝙿𝙰𝙲𝙴](#create-a-log-analytics-workspace)
- [𝙰𝙲𝚃𝙸𝚅𝙰𝚃𝙴 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻](#activate-microsoft-sentinel)
- [1 𝙷𝙾𝚄𝚁 𝚁𝙴𝚂𝚄𝙻𝚃𝚂](#1-hour-results)
- [𝙻𝙾𝙶 𝙴𝙽𝚁𝙸𝙲𝙷𝙼𝙴𝙽𝚃 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻](#log-enrichment-in-microsoft-sentinel)
- [𝙲𝚁𝙴𝙰𝚃𝙸𝙽𝙶 𝙰 𝙼𝙰𝙿 𝚆𝙾𝚁𝙺𝙱𝙾𝙾𝙺 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻](#creating-a-map-workbook-in-microsoft-sentinel)
- [24 𝙷𝙾𝚄𝚁 𝚁𝙴𝚂𝚄𝙻𝚃𝚂](#24-hour-results)
- [𝚃𝙾𝙿 5 𝙲𝙾𝚄𝙽𝚃𝚁𝙸𝙴𝚂](#top-5-countries)
- [𝚃𝙾𝙿 10 𝙰𝚃𝚃𝙰𝙲𝙺𝙴𝚁 𝙸𝙿 𝙰𝙳𝙳𝚁𝙴𝚂𝚂𝙴𝚂](#top-10-attacker-ip-addresses)
- [𝙵𝙰𝙸𝙻𝙴𝙳 𝙻𝙾𝙶𝙾𝙽 𝙰𝚃𝚃𝙴𝙼𝙿𝚃𝚂 𝚃𝙸𝙼𝙴𝙻𝙸𝙽𝙴](#failed-logon-attempts-timeline)
- [𝙲𝚁𝙴𝙰𝚃𝙸𝙽𝙶 𝙰 𝙲𝚄𝚂𝚃𝙾𝙼 𝙳𝙴𝚃𝙴𝙲𝚃𝙸𝙾𝙽 𝚁𝚄𝙻𝙴](#creating-a-custom-detection-rule)
- [𝙸𝙽𝙲𝙸𝙳𝙴𝙽𝚃 𝚁𝙴𝚂𝙿𝙾𝙽𝚂𝙴 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻](#incident-response-in-microsoft-sentinel)
- [𝙲𝙻𝙾𝚂𝙸𝙽𝙶 𝙾𝚄𝚃 𝚃𝙷𝙴 𝙸𝙽𝙲𝙸𝙳𝙴𝙽𝚃 𝙽𝚄𝙼𝙱𝙴𝚁 1](#closing-out-the-incident-number-1)

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

---

### Step 2: Select Your `Log Analytics Workspace` and `Add`

<img width="1173" height="124" alt="Lab 7" src="https://github.com/user-attachments/assets/e41d901e-57a8-4bfa-8406-a226fb2f9faa" />

---

### Step 3: In `Microsoft Sentinel`, Install `Windows Security Events`  

```
Content Management
  └─ Content Hub  
Search: Security Event
  └─ ☑ Windows Security Events
    └─ Install
```

<img width="1634" height="984" alt="Lab 11" src="https://github.com/user-attachments/assets/763c4d83-7054-4995-9816-1663209543b5" />

---

### Step 4: Once installed, check `Windows Security Events` and click `Manage`

```
Windows Security Events
  └─ ☑ Windows Security Events via AMA
  └─ Open Connector Page
```

---

### Step 5: Create a `Data Collection Rule`

```
Basic

Rule Details
  └─ Rule Name: DC-willis
  └─ Subscription: Azure Subscription 1
  └─ Resource Group: RG-willis
```

```
Resources

Source
  └─ ☑ Azure Subscription 1
  └─ ☑ RG-willis
  └─ ☑ YourVictualMachine
```

```
Collect
  └─ All Security Events
```

```
Review + Create
  └─ Create (When Prompted)
```

- ### Open a second tab, go to `portal.azure.com` and search for `Virtual Machines`

```
YourVirtualMachine
  └─ Settings
    └─ Extensions + Applications
```

*Note: This is to check if the `AzureMonitorWindowsAgent` extension is installed. Any logs from the `honeypot` will now be sent to `Log Analytics Workspace`.*

---

# 1 𝙷𝙾𝚄𝚁 𝚁𝙴𝚂𝚄𝙻𝚃𝚂

### *This KQL query filters for failed logon attempts (`Event ID 4625`) that occurred within a one-hour window from `07:46 to 08:46 UTC` on `July 21, 2025`. It then displays key details like timestamp, account, computer, eventID, activity, and IP address, sorted in chronological order.*

```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated between (datetime(2025-07-21T07:46:00Z) .. datetime(2025-07-21T08:46:00Z))
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
| sort by TimeGenerated asc
```
<img width="1047" height="746" alt="image" src="https://github.com/user-attachments/assets/a5ab9372-f4b4-452c-b5ee-63f07a9fa367" />

### *In the first hour after the honeypot VM went live, there were `94` failed login attempts originating from three unique IP addresses: `142.127.226.188`, `91.238.181.94`, and `80.94.95.75`. This early activity confirms that the exposed VM is already attracting external attention.*

---

# 𝙻𝙾𝙶 𝙴𝙽𝚁𝙸𝙲𝙷𝙼𝙴𝙽𝚃 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻

### Step 1: In Azure Portal, search for `Microsoft Sentinel` 

---

### Step 2: In `Microsoft Sentinel`, select the `Log Analytics Workspace` 

```
Microsoft Sentinel
  └─ Configuration
    └─ Watchlist
      └─ + New
```

---

### Step 3: Create a `Watchlist`

```
General
  └─ Name: geoip
  └─ Alias: geoip
```

```
Source
  └─ Browse for Files: geoip-summarized (Excel Spreadsheet)
  └─ SearchKey: Network
```

```
Review + Create
  └─ Create (When Prompted)
```

<img width="784" height="364" alt="Lab 51" src="https://github.com/user-attachments/assets/45e08b88-0185-4323-a390-fe52dd31dc62" />

---

### *This query filters failed login attempts (`Event ID 4625`) from the IP address `142.127.226.188`, then enriches the results with `GeoIP` data such as `city`, `country`, and `coordinates`.*

```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");
let WindowsEvents = SecurityEvent
    | where IpAddress == "142.127.226.188"
    | where EventID == 4625
    | order by TimeGenerated desc;
WindowsEvents
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| project TimeGenerated, Computer, AttackerIp = IpAddress, cityname, countryname, latitude, longitude
```

<img width="1046" height="710" alt="Lab 52" src="https://github.com/user-attachments/assets/8fce71cf-9edc-46ee-8220-e8e7d6a4350e" />

---

# 𝙲𝚁𝙴𝙰𝚃𝙸𝙽𝙶 𝙰 𝙼𝙰𝙿 𝚆𝙾𝚁𝙺𝙱𝙾𝙾𝙺 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻

### Step 1: In Azure Portal, search for `Microsoft Sentinel` 

---

### Step 2: Add a `Workbook`, in `Microsoft Sentinel`

```
Microsoft Sentinel
  └─ Threat Management
    └─ Workbooks
      └─ + Add Workbook
```

---

### Step 3: Create a new `Workbook`

```
New Workbook
  └─ Edit
    └─ Remove Prepopulated Content
      └─ + Add
        └─ Add Query
```

<img width="815" height="713" alt="Lab 54" src="https://github.com/user-attachments/assets/4ff54676-f319-45ea-8d17-8e11e9d346af" />

### *On the `Advanced Editor` Tab, copy and paste the `json`, then click `Done Editing`.*

```json
{
	"type": 3,
	"content": {
	"version": "KqlItem/1.0",
	"query": "let GeoIPDB_FULL = _GetWatchlist(\"geoip\");\nlet WindowsEvents = SecurityEvent;\nWindowsEvents | where EventID == 4625\n| order by TimeGenerated desc\n| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)\n| summarize FailureCount = count() by IpAddress, latitude, longitude, cityname, countryname\n| project FailureCount, AttackerIp = IpAddress, latitude, longitude, city = cityname, country = countryname,\nfriendly_location = strcat(cityname, \" (\", countryname, \")\");",
	"size": 3,
	"timeContext": {
		"durationMs": 2592000000
	},
	"queryType": 0,
	"resourceType": "microsoft.operationalinsights/workspaces",
	"visualization": "map",
	"mapSettings": {
		"locInfo": "LatLong",
		"locInfoColumn": "countryname",
		"latitude": "latitude",
		"longitude": "longitude",
		"sizeSettings": "FailureCount",
		"sizeAggregation": "Sum",
		"opacity": 0.8,
		"labelSettings": "friendly_location",
		"legendMetric": "FailureCount",
		"legendAggregation": "Sum",
		"itemColorSettings": {
		"nodeColorField": "FailureCount",
		"colorAggregation": "Sum",
		"type": "heatmap",
		"heatmapPalette": "greenRed"
		}
	}
	},
	"name": "query - 0"
}
```

```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");
let WindowsEvents = SecurityEvent;
WindowsEvents | where EventID == 4625
| order by TimeGenerated desc
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| summarize FailureCount = count() by IpAddress, latitude, longitude, cityname, countryname
| project FailureCount, AttackerIp = IpAddress, latitude, longitude, city = cityname, country = countryname,
friendly_location = strcat(cityname, " (", countryname, ")");
```

<img width="1145" height="603" alt="Lab 56" src="https://github.com/user-attachments/assets/ef0ca5ef-7add-4057-960e-c610299ac87c" /></br>

### *The map workbook has been created! I named this workbook `Windows VM Attack Map` and saved it to my resource group for future observations.* 

---

# 24 𝙷𝙾𝚄𝚁 𝚁𝙴𝚂𝚄𝙻𝚃𝚂

### *This KQL query filters for failed login attempts (`Event ID 4625`) targeting the `honeypot VM` over a `24-hour` period starting on `July 21, 2025`, at `07:46 UTC`. Surprisingly, the results revealed `107,836` failed logon attempts!*

```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated between (datetime(2025-07-21T07:46:00Z) .. datetime(2025-07-22T07:46:00Z))
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
| count
```

<img width="1936" height="837" alt="Lab 11" src="https://github.com/user-attachments/assets/412ec00c-824c-4a4f-8d10-ae2ad22e8469" />

---

## 𝚃𝙾𝙿 5 𝙲𝙾𝚄𝙽𝚃𝚁𝙸𝙴𝚂

```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");
let WindowsEvents = SecurityEvent
| where EventID == 4625
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| where isnotempty(countryname);
let Top5Countries = 
    WindowsEvents
    | summarize FailureCount = count() by countryname
    | top 5 by FailureCount desc
    | project countryname;
WindowsEvents
| where countryname in (Top5Countries)
| summarize FailureCount = count(),
          latitude = any(latitude),
          longitude = any(longitude),
          city = any(cityname)
    by countryname
| extend friendly_location = strcat(city, " (", countryname, ")")
| project countryname, FailureCount, latitude, longitude, friendly_location
```

<img width="1571" height="829" alt="Extra 7" src="https://github.com/user-attachments/assets/44226dea-0a42-4563-926e-5b7fbf632376" />

---

## 𝚃𝙾𝙿 10 𝙰𝚃𝚃𝙰𝙲𝙺𝙴𝚁 𝙸𝙿 𝙰𝙳𝙳𝚁𝙴𝚂𝚂𝙴𝚂

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by AttackerIp = IpAddress
| sort by FailedAttempts desc
```

<img width="364" height="424" alt="Extra 8" src="https://github.com/user-attachments/assets/321bb612-079a-46da-90d3-887b46d48414" />

---

## 𝙵𝙰𝙸𝙻𝙴𝙳 𝙻𝙾𝙶𝙾𝙽 𝙰𝚃𝚃𝙴𝙼𝙿𝚃𝚂 𝚃𝙸𝙼𝙴𝙻𝙸𝙽𝙴

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by bin(TimeGenerated, 1h)
| render columnchart
```

<img width="1951" height="739" alt="Extra 10" src="https://github.com/user-attachments/assets/195ef539-1f7e-4bb9-8289-170fd21db8ec" />

<img width="1951" height="735" alt="Extra 11" src="https://github.com/user-attachments/assets/50138024-90df-48dc-82f5-e0c515d97f28" />

---

# 𝙲𝚁𝙴𝙰𝚃𝙸𝙽𝙶 𝙰 𝙲𝚄𝚂𝚃𝙾𝙼 𝙳𝙴𝚃𝙴𝙲𝚃𝙸𝙾𝙽 𝚁𝚄𝙻𝙴

### Step 1: In Azure Portal, search for `Microsoft Sentinel`

---

### Step 2: Add an `Analytics Rule`, in `Microsoft Sentinel`

```
Microsoft Sentinel
  └─ Configuration
    └─ Analytics
      └─ + Create
```

### Step 3: Create a new `Scheduled Rule`

```
Analytics Rule Details
  └─ Name: Failed Logon Attempts
  └─ Description: This rule detects Windows logon failures on CORP-NET-EAST
  └─ Severity: Medium
  └─ MITRE ATT&CK
    └─ Credential Access
       └─ T1110 - Brute Force
    └─ Initial Access
       └─ T1078 - Valid Accounts
    └─ Reconnaissance
       └─ T1589 - Gather Identity Information
          └─ T1589.001 - Credentials
  └─ Status: Enabled
```

```kql
SecurityEvent
| where EventID == 4625
| where computer == "CORP-NET-EAST"
| summarize AttemptCount = count() by IpAddress, Account, Computer, bin(TimeGenerated, 5m)
| where AttemptCount > 3
```

```
Alert Enhancement
  └─ Account
    └─ Name - Account
  └─ Host
    └─ HostName - Computer
  └─ IP
    └─ Address - IpAddress
```

```
Query Scheduling
  └─ Run Query Every: 5 Minutes
  └─ Lookup Data: 5 Minutes
  └─ Start Running: Automatically
Alert Threshold
  └─ Generate Alert When Number of Query Results: Is Greater Than 0
Event Grouping
  └─ Group all events into a single alert
Suppression
  └─ Stop running query after alert is generated: On
  └─ Stop running query for: 24 Hours
Review + Create
  └─ Create (When Prompted)
```

<img width="1963" height="587" alt="Lab 65" src="https://github.com/user-attachments/assets/2320310c-5d60-4bd6-a0a7-a63262ae7f37" />

---

# 𝙸𝙽𝙲𝙸𝙳𝙴𝙽𝚃 𝚁𝙴𝚂𝙿𝙾𝙽𝚂𝙴 𝙸𝙽 𝙼𝙸𝙲𝚁𝙾𝚂𝙾𝙵𝚃 𝚂𝙴𝙽𝚃𝙸𝙽𝙴𝙻

### Step 1: In Azure Portal, search for `Microsoft Sentinel`

---

### Step 2: Investigate `Incidents` triggered by `Analytics Rule`

```
Microsoft Sentinel
  └─ Threat Management
    └─ Incident
```

<img width="575" height="742" alt="Extra 12" src="https://github.com/user-attachments/assets/5b066cfa-d2c0-467c-ad06-53c85c0525e1" />

---

### *An account named `\EAST` from IP address `80.94.95.43` attempted to log in to the computer `CORP-NET-EAST` `10,470` times, indicating a `brute-force` attempt.*

<img width="828" height="456" alt="Lab 70" src="https://github.com/user-attachments/assets/5c0e0b3e-b132-4c3b-a32e-5ad81f392c78" />

---

### *Further investigation revealed that the IP address originates from `Maarn, Netherlands`, with coordinates approximately at `latitude 52.0672` and `longitude 5.3781`.*

```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");
let WindowsEvents = SecurityEvent
    | where IpAddress == "80.94.95.43"
    | where EventID == 4625
    | order by TimeGenerated desc;
WindowsEvents
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| project TimeGenerated, Computer, AttackerIp = IpAddress, cityname, countryname, latitude, longitude
```

<img width="972" height="188" alt="Extra 15" src="https://github.com/user-attachments/assets/5cd10d8a-6eb9-4358-877b-c044ed60acfa" />

---

### *This IP address has been reported `43` times and flagged as malicious by several reputable security vendors, including `AlphaMountain.ai`, `CyRadar`, and `Fortinet`.*

<img width="1308" height="523" alt="Extra 13" src="https://github.com/user-attachments/assets/604a4cd9-c7d6-4d7e-9986-ac1c91e2f517" /></br>

<p = align=center>
<img width="502" height="494" alt="Extra 14" src="https://github.com/user-attachments/assets/0fe2b512-1039-47bd-b3f2-361d204d2734" />
</p>

---

### *The IP address `80.94.95.43` has not recorded any successful login attempts (`Event ID: 4624`), confirming that the computer `CORP-NET-EAST` remains uncompromised.*

```kql
let GeoIPDB_FULL = _GetWatchlist("geoip");
let WindowsEvents = SecurityEvent
    | where IpAddress == "80.94.95.43"
    | where EventID == 4624
    | order by TimeGenerated desc;
WindowsEvents
| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)
| project TimeGenerated, Computer, AttackerIp = IpAddress, cityname, countryname, latitude, longitude
```

<img width="363" height="97" alt="Extra 16" src="https://github.com/user-attachments/assets/c1f5eb42-6884-4756-95b1-360588270cf3" />

---

### Step 3: Block The Malicious IP Address

- ### Search for `Virtual Machines`

```
YourVirtualMachine
  └─ Networking
    └─ Networking Settings
```

- ### `+ Add` a new `Inbound Security Rule`

```
Add Inbound Security Rule
  └─ Source: IP Addresses
  └─ Source IP Addresses/CIDR Ranges: 80.94.95.0/24
  └─ Source Port Ranges: *
  └─ Destination: Any
  └─ Service: Custom
  └─ Destination Port Ranges: *
  └─ Protocol: Any
  └─ Action: Deny
  └─ Priority: 100
  └─ Name: Deny--80.94.95.0-24
```

<img width="2124" height="520" alt="Lab 1" src="https://github.com/user-attachments/assets/0325f06d-2753-4c5f-a6f4-940de9e06bf2" /></br>

### *The CIDR block `80.94.95.0/24` effectively covers all IP addresses from `80.94.95.0` to `80.94.95.255`. Implementing this as an `NSG` rule successfully blocked `80.94.95.43` and any other IPs within the `80.94.95.*` range from attempting to access the honeypot.*

---

## 𝙲𝙻𝙾𝚂𝙸𝙽𝙶 𝙾𝚄𝚃 𝚃𝙷𝙴 𝙸𝙽𝙲𝙸𝙳𝙸𝙴𝙽𝚃 𝙽𝚄𝙼𝙱𝙴𝚁 1

<img width="543" height="677" alt="Lab 77" src="https://github.com/user-attachments/assets/148e6c09-a7e3-42f7-8a3c-7d74f6d19fea" />

---

*Thank you for reading this far! Here’s a quick project summary: I deployed a `honeypot` in `Microsoft Azure` by intentionally exposing it to the public internet. To simulate a `Security Operations Center` (SOC), I created a `Log Analytics Workspace` and integrated it with `Microsoft Sentinel` to collect and analyze logs from the honeypot. Over a `24-hour` period, I monitored failed logon attempts—tracking the total volume (`107,836`), identifying the top five source countries and top ten attacking IP addresses, and visualizing the activity over time. I then created a custom detection rule and responded to a confirmed brute-force attack incident. This project aimed to build practical skills in monitoring, detecting, and responding to security threats to simulate real-world SOC operations.*

**Created By:** `Briana Willis`  
**Date:** `2025-07-22`  
**Time:** `19:21 UTC`
