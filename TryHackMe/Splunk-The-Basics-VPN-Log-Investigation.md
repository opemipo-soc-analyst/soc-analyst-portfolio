# Splunk: The Basics – VPN Log Investigation

## Platform
TryHackMe – SOC Level 1 Path  
Room: Splunk: The Basics  

---

## Objective

The purpose of this lab was to develop foundational skills in using Splunk as a Security Information and Event Management (SIEM) platform.  

The focus was on constructing search queries using Splunk Processing Language (SPL), filtering log data, and interpreting VPN connection events within a structured dataset.

---

## Scenario Overview

In this exercise, I investigated VPN connection logs to identify activity associated with a specific source IP address.

Target Source IP: 107.3.206.58

The objective was to retrieve all related events and analyze the connection details to determine whether the activity appeared normal or required further investigation.

---

## Search Query Used

source="VPN-logs-166359335514.json" host="VPN_Connections" Source_ip="107.3.206.58"

---

## Query Breakdown

* source= filters the specific log file

* host= narrows results to VPN connection logs

* Source_ip= filters events associated with the target IP address

This approach ensures precise log retrieval instead of broad or inefficient searches.

---

## Results Summary

The search returned the following:

* Total Events Identified: 14

* Source Country: United States

* Username Observed: Will Smith

* Destination Port: 443

* Protocol: TCP

* Action Field: teardown

* Log Index: VPN_Logs

---

## Log Interpretation

The action: teardown field indicates that the VPN session was successfully terminated.

Port 443 suggests encrypted communication over HTTPS, which is typical for VPN traffic.

While no explicit malicious indicators were observed in this dataset, repeated connections from a single source IP should always be evaluated in context.

Potential red flags to investigate further in a real SOC environment would include:

* Multiple failed authentication attempts (Event ID 4625 in Windows logs)

* Logins occurring outside normal business hours

* Suspicious geolocation patterns

* High frequency of connection attempts within a short time window

* Unusual data transfer volumes

---

## Recommended Next Steps (Real SOC Workflow)

If this activity were flagged in a production environment, the next investigative steps would include:

* Checking IP reputation using threat intelligence platforms (e.g., VirusTotal).

* Reviewing authentication logs for failed login attempts.

* Correlating activity across other endpoints.

* Using time-based filtering to analyze frequency patterns.

* Determining whether the username activity aligns with expected business behavior.

---

## Skills Demonstrated

This lab reinforced the following competencies:

* Constructing SPL queries in Splunk

* Filtering logs by host and source IP

* Interpreting structured VPN log data

* Understanding connection lifecycle events

* Applying investigative reasoning within a SIEM platform

* Thinking beyond alerts to validate potential risk

---

## Key Takeaway

Effective SOC analysts must go beyond simply viewing logs.

This exercise demonstrates the ability to:

* Narrow search scope using SPL

* Extract meaningful fields from raw log data

* Interpret connection behavior

* Apply contextual analysis before drawing conclusions

* This forms the foundation for more advanced threat detection and correlation techniques.

---

## Screenshot Evidence

### Splunk Logs
![Splunk Logs]
