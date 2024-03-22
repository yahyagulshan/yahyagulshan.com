---
title: "Add DMARC Policy in Route53 "
date: 2024-03-22T04:06:22Z
author:
authorLink:
description:
tags:
- DMARC
- Route53
- AWS
- Policy

categories:

draft: false
hiddenFromHomePage: true
---
# Secure Your Domain: Adding a DMARC Policy with AWS Route53🔏
### 1- Introduction 👋

* In today's digital world, protecting your domain from email spoofing and phishing attacks is crucial. 

* DMARC (Domain-based Message Authentication, Reporting & Conformance) is a powerful email authentication protocol that helps ensure only authorized senders can use your domain name. 

* By implementing a DMARC policy, you gain valuable insights into email traffic and protect your reputation.

**Are you using AWS Route53 for DNS management** ❓

📢 Great news! You can easily add a DMARC policy to your domain using Route53. Let's explore the steps involved:

### 2- Adding a DMARC Policy in Route53:📋

**1- Log in to your AWS Management Console**👨‍💻

**2- Navigate to Amazon Route53.** ⬅️

**3- Select the hosted zone for the domain you want to protect.** 🤺

**4- Click "Create Record Set**🖱️

**5- For Name, enter "_dmarc" (underscore followed by "dmarc").**

**6- For Type, choose "TXT".**

**7- For Value, paste the following DMARC policy string**📃

     v=DMARC1; p=quarantine; rua=mailto:noreply@abc.com; pct=100;

### 3- Explanation of the policy string: 🚏

* `v=DMARC1` specifies the DMARC version.

* `p=quarantine`  instructs email receivers to quarantine emails that fail DMARC checks. You can adjust this policy (e.g., p=reject) later based on your needs.

* `rua=mailto:noreply@abc.com` sets the email address to receive DMARC reports. `Replace noreply@abc.com` with a valid email address you control.

* `pct=100` indicates that DMARC reports should be sent for all emails (100%).

### 4- Set the TTL (Time To Live) to a low value, such as 60 seconds.

**Verifying DMARC Implementation:** ☑️🕵🏼‍♀️

* 1- Visit https://mxtoolbox.com/dmarc.aspx.

* 2- Enter your domain name in the search bar and click "Lookup."

* 3- Check for a DMARC record. It may take some time for the record to propagate across the internet.

**🥳🥳Congratulations!🥳🎉👏**  You've successfully implemented a DMARC policy for your domain using AWS Route53. Monitoring DMARC reports and adjusting your policy over time will help you further enhance email security and prevent unauthorized use of your domain.


**Additional Tips:**

Start with a monitoring-only policy (p=none) to understand email traffic patterns before enforcing stricter actions.
Consider using a DMARC record generator tool for more complex policy configurations.
Regularly monitor DMARC reports to identify any suspicious activity or delivery issues.
By following these steps and maintaining your DMARC policy, you can significantly improve email security and protect your domain reputation.