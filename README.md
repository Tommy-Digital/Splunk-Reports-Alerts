# Splunk-Reports-and-Alerts

<p align="center">
  <img width="460" height="300" src=![Splunk Cover](//github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/d7b58e2a-8de6-4859-ac8b-fc1e6cfa5f6d)>
</p>
![Splunk Cover](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/d7b58e2a-8de6-4859-ac8b-fc1e6cfa5f6d)

Vandalay Industries uses Splunk for their security monitoring and have been experiencing a variety of security issues against their online systems over the past few months.

My objective was to utilize Splunk to design a monitoring solution to protect Vandalay from security attacks.

As an SOC analyst, I was tasked with developing searches, custom reports, and alerts to monitor Vandalay's security environment in order to protect them from future attacks.

  As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandalay has been experiencing DDOS attacks against their web servers.
Not only were Vandalay web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Our networking team provided results of a network speed run around the time of the latest DDOS attack.

For monitoring activity, I created a report that determined the impact of the DDOS attack by creating a field that calculated the ratio on the upload/download speeds.
# host="server_speedtest.csv" | eval ratio=(DOWNLOAD_MEGABITS/UPLOAD_MEGABITS)
![1  splunk search](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/24355487-d43d-40a6-89f4-450328db0821)
![1 1 splunk search results](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/a0a2e677-d893-43c1-b77b-e34d31203b4f)

I added my results to a table including a timestamp, IP address, and ratio between speeds.
# host="server_speedtest.csv" | eval ratio=(DOWNLOAD_MEGABITS/UPLOAD_MEGABITS) | table DOWNLOAD_MEGABITS, UPLOAD_MEGABITS, _time, ratio, IP Address"
![2  splunk search](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/d77aae43-a04e-4973-9bcc-92abf81f0ddf)


My report showed that the attack happened on February 23rd, 2020 from about 2:00 P.M. to 8:00 P.M. It took our systems roughly 6 hours to recover back to an average speed ratio.
![2 1 splunk search results](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/ff147475-9530-4a7c-b1f2-a0346f054a65)


Since Vandalay uses Nessus vulnerability scanners, we have pulled the last 24 hours of scans to see if there are any critical vulnerabilities. Due to the frequency of attacks, the manager needs to be sure that sensitive customer data on the servers is not vulnerable.
![3 Vulnerabilities](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/fb6ab9c8-7111-4f1b-9990-4e0fb409c09b)

To ensure our manager, we created a report that determined the amount of critical vulnerabilities existing on the server. If any more critical vulnerabilities re-appear an alert has now been created to send an email notification to our SOC team so that the vulnerability
can be assesed and properly handled to prevent any risk to the customer data server. 

![3 1 Alert Parameters](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/b6556400-6342-4742-a7c1-2da5c872ead4)
![3 2 Vuln Scan Nessus alert](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/4149e879-6621-455f-8358-50374f28ccef)


A Vandalay server has also been experiencing brute force attacks into the administrator account. Management has instructed us to setup monitoring and concurrently notify the SOC team in the event of a brute force attack happening again. 
# host="Administrator_logs.csv" user=ADMINISTRATOR EventCode=4625
![4 0 brute force search](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/1449ce65-692f-4153-b7bb-6b61028d52f1)


We used our administrator logs that documented a previous brute force attack to create a baseline of the average amount of bad login attempte from the administrator. The previous attack appears to have occured on February 21st of 2020 around roughly 5:00 P.M. 
This analysis helped us to determine a good threshold that indicates if a brute force attack is occurring. There was a combined total of 469 events from the administrative account failing to login between February 20-21st. Across the 469 events, the baseline average 
for seemingly normal activity was 13 events. This helped our decision-making to place our threshold at 17 attempts.  


![4 1 Alert Breakdown](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/39cc97ad-c508-4645-8c51-c1899d8a3aa0)
![4 2 Brute Force Breakdown Cont](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/ca164089-5ea4-42a0-8a06-b5f451f4a3d0)
![4 3 Brute Force Alert Parameters](https://github.com/Tommy-Digital/Splunk-Reports-Alerts/assets/149236559/2d07809a-b943-441c-8447-e0685f52b358)

