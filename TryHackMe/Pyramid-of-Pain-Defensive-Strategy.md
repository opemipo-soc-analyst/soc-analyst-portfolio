# Pyramid of Pain – Defensive Detection Strategy

**Platform:** TryHackMe  
**Path:** SOC Level 1  
**Room:** Pyramid of Pain  
**Focus Area:** Detection Strategy & Defensive Thinking  

---

## 📌 Introduction

The **Pyramid of Pain** is a cybersecurity model that explains how difficult it is for adversaries to change different types of indicators when defenders detect them.

The higher up the pyramid defenders operate, the more operational cost and disruption is inflicted on attackers.

This room emphasizes an important defensive mindset shift:

> Detecting behavior is stronger than blocking indicators.

---

## 🧱 Pyramid Levels Explained

Below are the levels of the Pyramid of Pain, from least painful (easy to change) to most painful (hardest to change).

---

### 1️⃣ Hash Values (Least Painful)

- File hashes (MD5, SHA1, SHA256)
- Unique fingerprint of a file

**Why it’s weak:**
Attackers can slightly modify malware or recompile it to generate a new hash.

**Defensive value:**
Useful for identifying known malware, but not reliable for long-term detection.

---

### 2️⃣ IP Addresses

- Malicious C2 server IPs
- Hosting infrastructure

**Why it’s weak:**
Attackers can easily rotate IP addresses or switch hosting providers.

**Defensive value:**
Helpful for short-term blocking but not strategic detection.

---

### 3️⃣ Domain Names

- Phishing domains
- Malware distribution domains

**Why it’s moderate:**
Attackers must register new domains, but this process is still relatively easy.

**Defensive value:**
Effective when combined with DNS monitoring and threat intelligence feeds.

---

### 4️⃣ Network Artifacts

- Suspicious URI patterns
- Unusual HTTP headers
- Beaconing intervals
- C2 communication patterns

**Why it’s stronger:**
Attackers must modify communication methods and traffic behavior.

**Defensive value:**
Network behavior monitoring improves detection of persistent threats.

---

### 5️⃣ Host Artifacts

- Registry modifications
- File system changes
- Scheduled tasks
- Persistence mechanisms

**Why it’s stronger:**
Changing persistence techniques requires attackers to redesign parts of their attack.

**Defensive value:**
EDR solutions rely heavily on host artifact detection.

---

### 6️⃣ Tools

- Exploitation frameworks
- Malware families
- PowerShell scripts
- Credential dumping tools

**Why it’s painful:**
If defenders detect tool-based patterns, attackers must switch tools or heavily modify them.

**Defensive value:**
Detection engineering targeting tool behavior increases attacker workload.

---

### 7️⃣ TTPs (Tactics, Techniques, and Procedures) – Most Painful

- Execution techniques
- Privilege escalation methods
- Lateral movement strategies
- Persistence mechanisms

**Why this is most painful:**
TTPs represent how attackers operate.

If defenders detect behavioral patterns rather than static indicators:

- Attackers must redesign their attack chain
- Re-test payloads
- Rebuild infrastructure
- Invest more time and resources

This significantly increases operational cost.

---

## 🛡️ Practical SOC Application

In a real SOC environment:

**Weak detection approach:**
Block a malicious IP address.

**Stronger detection approach:**
Alert on abnormal PowerShell execution with encoded commands and suspicious parent process.

The second approach focuses on attacker behavior, not infrastructure.

This aligns with higher levels of the Pyramid of Pain and provides long-term defensive advantage.

---

## 🔎 Key Takeaways

- Not all indicators provide equal defensive value.
- Low-level IOCs (hashes, IPs) are easy for attackers to change.
- Behavioral detection is more effective long-term.
- TTP-focused detection increases attacker operational cost.
- Modern SOC operations should prioritize technique-based detection over static blocking.

---

## 🎯 Conclusion

The Pyramid of Pain shifts defensive strategy from:

**"Blocking what the attacker uses"**

to

**"Detecting how the attacker operates."**

Understanding this model improves detection engineering, incident response effectiveness, and overall SOC maturity.

---

