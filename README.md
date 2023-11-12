# Splunk-Reports-and-Alerts

Vandalay Industries uses Splunk for their security monitoring and have been experiencing a variety of security issues against their online systems over the past few months.

My objective was to utilize Splunk to design a monitoring solution to protect Vandalay from security attacks.

As an SOC analyst, I was tasked with developing searches, custom reports, and alerts to monitor Vandalay's security environment in order to protect them from future attacks.

  As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandalay has been experiencing DDOS attacks against their web servers.
Not only were Vandalay web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Our networking team provided results of a network speed run around the time of the latest DDOS attack.

For monitoring activity, I created a report that determined the impact of the DDOS attack by creating a field that calculated the ratio on the upload/download speeds.

My report showed that the attack happened on February 23rd, 2020 from about 2:00 P.M. to 8:00 P.M. It took our systems roughly 6 hours to recover back to an average speed ratio.







Since Vandalay uses Nessus vulnerability scanners, we have pulled the last 24 hours of scans to see if there are any critical vulnerabilities. Due to the frequency of attacks, the manager needs to be sure that sensitive customer data on the servers is not vulnerable.

To ensure our manager, we created a report that determined the amount of critical vulnerabilities existing on the server. If any more critical vulnerabilities re-appear an alert has now been created to send an email notification to our SOC team so that the vulnerability
can be assesed and properly handled to prevent any risk to the customer data server. 






A Vandalay server has also been experiencing brute force attacks into the administrator account. Management has instructed us to setup monitoring and concurrently notify the SOC team in the event of a brute force attack happening again. 

We used our administrator logs that documented a previous brute force attack to create a baseline of the average amount of bad login attempte from the administrator. The previous attack appears to have occured on February 21st of 2020 around roughly 5:00 P.M. 
This analysis helped us to determine a good threshold that indicates if a brute force attack is occurring. There was a combined total of 469 events from the administrative account failing to login between February 20-21st. Across the 469 events, the baseline average 
for seemingly normal activity was 13 events. This helped our decision-making to place our threshold at 17 attempts.  
