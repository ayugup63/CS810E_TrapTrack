# CS810E_Project
Experimental Setup
To evaluate the TrapTrack system, experiments were conducted across multiple environments using a consistent setup for browser automation, network interception, and data analysis.
Tools used and their versions
•	Operating Systems:
 	Windows 11
 	MacOS

•	Programming Language:
 	Python 3.12.3
•	Key Software and Tools:
 	playwright (v1.39+) 
 	mitmproxy (v10.0) 
 	Geo-Location API – http://ip-api.com to resolve IP addresses found in network logs to country-level geographic locations.
•	Test Sites:
 	 https://www.amazon.co.uk 
 	 https://www.euronews.com
•	Python Standard and external Libraries
 	os,  subprocess, json, sys
 	pathlib
 	webbrowser, csv
 	time, datetime





Procedure

Step 1: Install Tools and Libraries
Ensure that all tools and libraries mentioned in the previous section are properly installed before execution.

Step 2: Prepare Test Inputs 
Edit the test_sites.csv file to include two columns: Website and ConsentType.
Example:
Website,ConsentType  
https://www.amazon.co.uk,EU

Step 3: Start mitmdump for Traffic Logging
Launch mitmdump in a terminal with the following command:
mitmdump -s network_logger.py

Step 4: Run the Main Experiment Script
In the terminal, execute the full pipeline using
python run_all.py

Step 5: What the Script does
The run_all.py script performs the following actions automatically, parallel we can browse the site and press enter once we are done browsing.
 	Loads each website from test_sites.csv
 	Simulates a browsing session using Playwright (we can navigate or browse as a user and press enter once you are done browsing)
 	Captures storage snapshots (cookies, localStorage, sessionStorage) before and after consent
 	Injects JavaScript to detect fingerprinting techniques
 	Logs all network traffic through mitmproxy
 	Resolves tracker IPs to country-level using Geo-IP
 	Calculates a normalized privacy risk score (TrapScore)
 	Generates a static HTML report summarizing all findings
  
Step 6: Output Review
After execution, examine the following output directories and files
 	data/network_logs/ – Contains logs of third-party tracker requests
 	data/storage_logs/ – Stores JSON snapshots of browser storage
 	data/geo_locations.json – IP-to-country resolution results
 	screenshots/ – Screenshots captured before and after consent
 	traptrack_report.html – Complete privacy analysis report

Step 7: Analyse the Results
 	Result can be analyzed, we can see before and after consent snapshots
 	Pre and Post consent cookies
 	GeoIP locations leaked
 	Final Summary and Risk Score
