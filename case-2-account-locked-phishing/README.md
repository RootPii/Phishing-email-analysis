# Case 2: Account Locked Phishing Email (Amazon Impersonation)

A suspicious email was identified claiming that the user's Amazon account had been locked. The objective of this analysis is to examine the email, extract useful artifacts, and verify whether it is a phishing attempt.

---

## Description:

At first glance, this email looks like a normal message from Amazon. It says there are some unusual changes in the account and asks the user to review it to continue using the services.

It also mentions a 72-hour deadline, which creates urgency. This is a common trick used in phishing emails to make users act quickly without thinking much.

---

## Email Details:

Sender: amazon@zyevantoby.cn  
Receiver: saintington73@outlook.com  
Date: Wed, 14 Jul 2021 01:40:32 +0900  
Subject: Your Account has been locked  

Return Path: amazon@zyevantoby.cn  
Sender IP: 45.156.23.138  
Reverse DNS Lookup: whois.ripe.net  

---

## URL:

hxxps://emea01[.]safelinks[.]protection[.]outlook[.]com/?url=https%3A%2F%2Famaozn[.]zzyuchengzhika[.]cn%2F%3Fmailtoken%3Dsaintington73%40outlook[.]com

---

## Analysis:

### Email Analysis:

Even though the email looks like it is from Amazon, the sender domain is clearly not related to Amazon. This is the first major red flag.

The message also tries to create pressure by saying the account will be affected within 72 hours. This kind of urgency is commonly used in phishing emails to push users into clicking links quickly.

---

### URL Analysis:

The URL was checked using VirusTotal, URL2PNG, and URLhaus.

At first, the link looks safe because it uses Microsoft SafeLinks. But SafeLinks is just a redirection service. If we decode or inspect the URL closely, it redirects to another domain:

hxxps://amaozn[.]zzyuchengzhika[.]cn

Here, the domain is trying to mimic "amazon" but contains a typo ("amaozn"), which is a common phishing technique.

In URL2PNG, the page could not be loaded. This usually means the site is no longer active, possibly because it was taken down after being reported.

URLhaus also shows that similar infrastructure has been associated with malicious activity in the past.

---

### Infrastructure Analysis:

The sender IP (45.156.23.138) is not linked to Amazon infrastructure. The reverse lookup points to a generic hosting provider (RIPE), which is often used by attackers.

This further confirms that the email is not legitimate.

---

## Conclusion:

Based on the sender domain, suspicious URL structure, use of SafeLinks redirection, and urgency in the message, this email is clearly a phishing attempt designed to trick users into giving their credentials.

---

## Defensive Measure:

Since the sender is not legitimate, it can be blocked at the email gateway without affecting normal operations.

The malicious URL and domain should also be blocked at DNS, proxy, or firewall level.

It is also important to search for similar emails with the same subject or sender to identify other affected users and warn them before they click the link.

User awareness is equally important, especially about checking sender domains, avoiding urgent messages, and verifying links before clicking.
