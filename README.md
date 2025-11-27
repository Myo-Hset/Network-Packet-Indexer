# Network-Packet-Indexer

## Objective 

The Detection Lab project was created to provide a controlled environment for simulating and detecting cyberattacks. Its primary focus was on ingesting and analyzing logs within a Security Information and Event Management (SIEM) system, while also generating test telemetry to replicate realistic attack scenarios. Through this process, the project enhanced understanding of network security, attack techniques, and defensive measures.

### Skills Learned

- Analyzed and interpreted network logs to identify relevant events.
- Used graphs to visualize IPs and network activity, gaining a clearer and more comprehensive overview.
- Developed skills in generating and recognizing attack signatures and patterns.
- Improved understanding of network protocols and common security vulnerabilities.
- Integrated OSINT tools into our environment for efficient data ingestion and enhanced threat analysis.

### Tools Used

- Arkime - Network capture analysis tool for examining network traffic.
- OSINT tools - Used urlscan.io to check IP and URL reputation
- MaxMind - Used MaxMind to retrieve GeoIP data and enrich IP-based analysis with geolocation information.
- Malware-Traffic-Analysis - Utilized Malware Traffic Analysis for creating and studying network traffic and malware behavior.
- Wireshark - Used Wireshark to capture and analyze relevant network packets

##Steps Taken

Step-1 - Setting Up the Arkime server

- After installing Ubuntu Server in a virtual machine, I established an SSH connection using PowerShell. This setup makes it easier to copy and paste commands.
- Download Arikme machine:

      wget https://github.com/arkime/arkime/releases/download/v5.1.2/arkime_5.1.2-1.ubuntu2204_amd64.deb

After finishing the download, install Arkime. Next, perform some basic configurations, such as creating a password and enabling MaxMind. MaxMind enriches IP addresses by providing geolocation data, which enhances the analysis.
Arkime is stored unter the /opt/ directory.

Go to :  **sudo /opt/arkime/bin/configure**  - Add you network ineterface. 

<IMAGE>
<IMG>

Run the command as hilighted Image. Once the configuration is complete, I should be able to access Arkime using my IP address on port 8005. But first, we need to create an account on MaxMind and obtain both the license key and the account ID.

<IMG> 

Go to the **/etc/GeoIP.conf** Change the Configure as Highledtd

Step - 2 Enrich the data using OSINT tools built into Arkime

We need to enable service in Arkime

      udo /opt/arkime/bin/Configure --cont3xt 
      
      sudo nano /opt/arkime/etc/cont3xt.ini

<IMG>

Modified the Configuration as Highleted and restart the Service

      systemctl restart arkimecont3xt.service and go on our localhost:3218

To integrate OSINT with Arkime, you need an API key, which is issued after creating an account with one of the supported OSINT tools.

<IMG> 

I have connected Arkime with VirusTotal, allowing me to check the VirusTotal score and view related information directly within Arkime content.


## Summary 

Arkime is a powerful network capture and analysis tool. When utilized effectively, it can enhance our capabilities and strengthen various use cases.





      


