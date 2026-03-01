🛠️ GitHub README: Splunk SIEM Lab
Project Name: Historical Apache Log Analysis & Security Dashboarding

Project Overview
In this lab, I performed end-to-end data ingestion, normalization, and visualization of historical Apache web server logs using Splunk Enterprise. The project involved solving complex timestamp extraction issues and building a functional security monitoring dashboard.

Challenges & Troubleshooting
Timestamp Correction: Initial ingestion failed because Splunk misinterpreted 2015 data as 2025. I applied an advanced TIME_FORMAT string (%d/%b/%Y:%H:%M:%S %z) to correctly parse the day, month, and year.

Historical Data Ingestion: Because the logs were older than Splunk's default 2,000-day limit, I created a custom MAX_DAYS_AGO setting of 10000 to allow the data to index properly.

Data Segregation: I practiced industry best practices by moving data out of the default index and into a dedicated apache-data index for better search performance.

Security Insights & Visualizations
HTTP Status Distribution: A pie chart showing the ratio of successful requests (200 OK) to client errors (404 Not Found), useful for spotting automated vulnerability scanners.

Top 10 Source IPs: A statistics table identifying the most active external actors, allowing for quick identification of potential brute-force or DDoS sources.
