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
The investigation revealed that the sender domain `amaz0n-pay.com` is a **typosquatted** version of the legitimate Amazon domain.  
The message also passed through **suspicious relay hosts** such as `smtp.ecorp.com` and `suspicious-host.ru`, both of which appeared in blacklist databases.  
The email even contained a **localhost hop**, showing that it did not originate from a proper mail server.  

All authentication mechanisms—SPF, DKIM, and DMARC—**failed**, confirming the sender was impersonating another entity.  
Although VirusTotal did not yet detect the domain as malicious, the combination of these findings strongly indicates a **phishing attempt using malicious infrastructure**.

**Final Verdict:** 🚨 The email is classified as **Phishing / Malicious Infrastructure**.

---

## 🧪 VirusTotal Summary
I uploaded the `.eml` file and searched its domains and IP addresses separately on VirusTotal.  
All returned “undetected,” which likely means the campaign was **new or had not yet been reported** by antivirus vendors.  
However, manual analysis showed clear signs of phishing, proving that analyst reasoning remains essential even when tools report no detections.

---

## ⚙️ Tool Correlation & Analysis
MXToolbox reported multiple blacklists and authentication failures, while VirusTotal showed no detections.  
This difference is expected because MXToolbox relies on DNS-based reputation and spam databases, which often detect abuse earlier.  
VirusTotal depends on antivirus signatures and uploaded samples, which may not exist yet for new campaigns.  
By correlating both results, I confirmed that the email was malicious despite the absence of AV detections.

---

## 🖼️ Screenshots
*(Add these when ready — they make your project stand out visually.)*

![Email Header Analysis](screenshots/header_analysis.png)
![MXToolbox Result](screenshots/mxtoolbox_result.png)
![VirusTotal Result](screenshots/virustotal_result.png)

---

## 🧠 Key Learnings
- How to manually analyze email headers and authentication mechanisms.  
- Identifying spoofed or typosquatted domains.  
- Using MXToolbox for DNS and blacklist verification.  
- Understanding why VirusTotal “undetected” does not always mean safe.  
- Correlating multiple tools to reach accurate conclusions as a SOC analyst.  

---

## 🔗 References
- [MXToolbox](https://mxtoolbox.com/)  
- [VirusTotal](https://www.virustotal.com/)  
- [Thunderbird Documentation](https://www.thunderbird.net/)  
- [Sublime Text Docs](https://www.sublimetext.com/docs/)  
- Udemy SOC Analyst Course – *Email & Phishing Analysis Module*
