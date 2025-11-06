# 🧾 Email & Phishing Analysis

## 📘 Overview
This project focuses on analyzing a **suspicious phishing email** to detect spoofed domains, authentication failures, and malicious infrastructure.  
The goal was to identify potential threats, verify findings using multiple tools, and document results in a structured SOC analyst format.

---

## 🧰 Tools & Technologies
- **Thunderbird** – Extracted and viewed the email as a `.eml` file.  
- **Sublime Text** – Manually analyzed email headers, message content, and authentication results.  
- **MXToolbox** – Verified domains, hosts, and authentication records (SPF, DKIM, DMARC).  
- **VirusTotal** – Checked domains and IP addresses for malware or phishing indicators.  

---

## 🧩 What I Did
I began by extracting the email using Thunderbird and saving it as a `.eml` file.  
Next, I opened it in Sublime Text to manually review key headers such as **From**, **Received**, and **Message-ID**, and inspected the authentication results (SPF, DKIM, and DMARC).

I then used **MXToolbox** to verify the sender information and check for any blacklisted domains or IPs. The tool confirmed that the sender’s mail host and localhost relay were blacklisted and that all authentication checks had failed.

Finally, I used **VirusTotal** to check the domains and IP addresses individually.  
Even though VirusTotal reported “undetected,” I concluded that this was a **new or low-profile phishing attempt** based on the red flags already found in the headers and MXToolbox results.

---

## 📊 Outcome
## Outcome

1. **Suspicious Domain:** `amaz0n-pay.com` — typosquatted version of Amazon Pay; undetected by vendors but linked to community reports describing requests for personal information and containing poor grammar/spelling.
2. **Suspicious Host:** `suspicious-host.ru` — appears on MXToolbox blacklists and is associated with the sending infrastructure.
3. **Origin IP:** `203.0.113.77` — not flagged by security vendors on VirusTotal but associated with at least one detected malicious file and connected to the blacklisted host.
4. **Localhost Hop:** The email passed through `127.0.0.1`, indicating forged routing.
5. **Authentication:** SPF failed, DKIM failed, DMARC failed.
6. **Conclusion:** This email is part of a **new or low-profile phishing campaign** impersonating Amazon Pay. Community reports and behavioral indicators (typosquatting, poor grammar/spelling, blacklisted relay) confirm the attack is malicious despite limited automated detections.


**Final Verdict:** 🚨 The email is classified as **Phishing / Malicious Infrastructure**.



## 🧪 VirusTotal Summary
I uploaded the `.eml` file and searched its domains and IP addresses separately on VirusTotal.  
All returned “undetected,” which likely means the campaign was **new or had not yet been reported** by antivirus vendors.  
However, manual analysis showed clear signs of phishing, proving that analyst reasoning remains essential even when tools report no detections.

### Domain Lookup (`amaz0n-pay.com`)
The domain `amaz0n-pay.com` was scanned on VirusTotal.

**Result:**  
No security vendors flagged this domain as malicious.

### IP Lookup (`203.0.113.77`)
The IP address `203.0.113.77` (associated with `suspicious-host.ru`) was scanned on VirusTotal.

**Result:**  
No security vendors flagged this IP address as malicious.


## 📸 Project Screenshots

### 1. Thunderbird Email
![Thunderbird Email](https://github.com/simisolajnr30/Email-and-Phising-Analysis/blob/main/screenshot/thunderbird_email.png?raw=true)

### 2. Sublime Text Analysis
![Sublime Analysis](https://github.com/simisolajnr30/Email-and-Phising-Analysis/blob/main/screenshot/sublime_analysis.png?raw=true)

### 3. MXTool Header Analyzer
![MXTool Header](https://github.com/simisolajnr30/Email-and-Phising-Analysis/blob/main/screenshot/mxtool_header_analyzer.png?raw=true)

### 4. VirusTotal Domain Lookup
![VirusTotal Domain Lookup](https://github.com/simisolajnr30/Email-and-Phising-Analysis/blob/main/screenshot/virustotal_domain_lookup.png?raw=true)

### 5. VirusTotal IP Address Lookup
![VirusTotal IP Lookup](https://github.com/simisolajnr30/Email-and-Phising-Analysis/blob/main/screenshot/virustotal_ip_address.png?raw=true)




---

## ⚙️ Tool Correlation & Analysis
MXToolbox reported multiple blacklists and authentication failures, while VirusTotal showed no detections.  
This difference is expected because MXToolbox relies on DNS-based reputation and spam databases, which often detect abuse earlier.  
VirusTotal depends on antivirus signatures and uploaded samples, which may not exist yet for new campaigns.  
By correlating both results, I confirmed that the email was malicious despite the absence of AV detections.

---



---

## 🧠 Key Learnings
- How to manually analyze email headers and authentication mechanisms.  
- Identifying spoofed or typosquatted domains.  
- Using MXToolbox for DNS and blacklist verification.  
- Understanding why VirusTotal “undetected” does not always mean safe.  
- Correlating multiple tools to reach accurate conclusions as a SOC analyst.  


