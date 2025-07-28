# `1 WEEK` RESULTS

### *This KQL query filters for failed login attempts (`Event ID 4625`) targeting the `honeypot VM` over a `1 week` period between `July 21, 2025` and `July 28, 2025`. Surprisingly, the results revealed `315,565` failed logon attempts!*

```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated between (datetime(2025-07-21T00:00:00Z) .. datetime(2025-07-28T23:59:59Z))
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
| count
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

<img width="1875" height="837" alt="Honey 2" src="https://github.com/user-attachments/assets/0b7965af-4212-4f22-966a-13d1730f5ad8" />

---

# `TOP 5 COUNTRIES`

### *This KQL query analyzes failed login attempts (`Event ID 4625`) by enriching the data with `IP geolocation` from a custom watchlist. It identifies the `top five countries` with the highest number of failed attempts, then summarizes and displays each country’s failure count along with geographic details like city, latitude, and longitude for visualization or threat analysis.*

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

<img width="1578" height="834" alt="Honey 3" src="https://github.com/user-attachments/assets/1a3f27f7-abbf-42b9-8750-385563254c9f" />

---

# `TOP 10 ATTACKER IP ADDRESSES`

### *This KQL query identifies the `IP addresses` responsible for the most failed login attempts (`Event ID 4625`) within the time range of `July 21 to July 28, 2025`. It filters the security event logs for that event ID and time window, then counts the number of failed attempts per IP address.. The results are sorted in descending order to highlight the IPs with the highest number of failed logins.*

```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated between (datetime(2025-07-21T00:00:00Z) .. datetime(2025-07-28T23:59:59Z))
| summarize FailedAttempts = count() by AttackerIp = IpAddress
| sort by FailedAttempts desc
```

<img width="323" height="388" alt="Honey 6" src="https://github.com/user-attachments/assets/ef56f187-d3a3-4fbb-861a-1442952140a7" />

---

# `FAILED LOGON ATTEMPTS TIMELINE`

```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated between (datetime(2025-07-21T00:00:00Z) .. datetime(2025-07-28T23:59:59Z))
| summarize FailedAttempts = count() by AttackerIp = IpAddress
| sort by FailedAttempts desc
```

<img width="2156" height="985" alt="Honey 5" src="https://github.com/user-attachments/assets/061e5a1d-4407-498a-b7c7-bfd535873790" />

### *The timeline illustrates the volume of failed login attempts over time, totaling `315K`, with several notable spikes. `July 21st` around `8 PM` remains the highest at `70,400` failed logon attempts.*

---

### *See the full project here:</br>[`Implementing a SOC and Honeypot in Microsoft Azure`](https://github.com/brianalwillis/soc-honeypot/tree/main)*
