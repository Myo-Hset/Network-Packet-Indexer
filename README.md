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

### Step-1 - Setting Up the Arkime server

- After installing Ubuntu Server in a virtual machine, I established an SSH connection using PowerShell. This setup makes it easier to copy and paste commands.
- Download Arikme machine:

      wget https://github.com/arkime/arkime/releases/download/v5.1.2/arkime_5.1.2-1.ubuntu2204_amd64.deb

After finishing the download, install Arkime. Next, perform some basic configurations, such as creating a password and enabling MaxMind. MaxMind enriches IP addresses by providing geolocation data, which enhances the analysis.
Arkime is stored unter the /opt/ directory.

<img width="1854" height="956" alt="image" src="https://github.com/user-attachments/assets/5ec8f0dd-0ab2-4766-81dd-06de90ea3d60" />

Then Go to :  **sudo /opt/arkime/bin/Configure**  - Add you network ineterface. 
<img width="948" height="85" alt="image" src="https://github.com/user-attachments/assets/f7b29a5c-05a4-45aa-9d9c-295a5caad2e5" />


<img width="771" height="27" alt="image" src="https://github.com/user-attachments/assets/5b092f8e-eacd-469b-806e-76ed07d38284" />

<img width="1862" height="221" alt="image" src="https://github.com/user-attachments/assets/922368e0-00f4-4911-9ad1-8ab8cd62173f" />

**Add the user**

<img width="1178" height="78" alt="image" src="https://github.com/user-attachments/assets/ae494011-76fb-4b30-b467-8b2aa2358c61" />

This is your server user password. I have used the same username, so don’t confuse it with the Arkime username.

<img width="840" height="277" alt="image" src="https://github.com/user-attachments/assets/cec7c28f-31ec-4a39-9e98-0c08f27fecf9" />

Run the command shown in the highlighted image. Once the configuration is complete, you will be able to access Arkime using your IP address on port 8005. Before that, however, you need to create an account on MaxMind and obtain both the license key and the account ID.

<img width="1903" height="583" alt="image" src="https://github.com/user-attachments/assets/87996600-7abb-4c3a-9d06-5a6f3809d370" />


Install GeoIP, Run : 

            sudo apt install geoipupdate

Go to the **/etc/GeoIP.conf** Change the Configure as Highlight, And RUn :

            sudo geoipupdate

            systemctl restart arkimecapture.service

### Step - 2 , Ingesting The PCAP files

I will ingesting the PCAP files form (https://www.malware-traffic-analysis.net/)
for Analysing

<img width="1876" height="475" alt="image" src="https://github.com/user-attachments/assets/f7085819-4ea8-47fb-9c4f-781b88249238" />

After download the PCAP file. To monitor it by Runing this command 

            sudo /opt/arkime/bin/capture --copy -m -R .


<img width="1335" height="99" alt="image" src="https://github.com/user-attachments/assets/cf4883d0-b502-42ca-84f7-633c22d1acf1" />

<img width="1899" height="484" alt="image" src="https://github.com/user-attachments/assets/e640a91f-e7d5-45fb-bc27-2e418af27756" />

New We can Clearly See the what is the PCAP Look like 

- Session View
<img width="1903" height="912" alt="image" src="https://github.com/user-attachments/assets/f59efa21-5849-44e5-a549-3a50d0132695" />

- SPIView
<img width="1903" height="910" alt="image" src="https://github.com/user-attachments/assets/f2a4412f-221f-46fb-aa5d-fe4003c28a93" />

- Connections View
<img width="1899" height="896" alt="image" src="https://github.com/user-attachments/assets/e406f883-1d6d-4e66-b12f-bb7024f0cbf2" />



### Step - 3 Enrich the data using OSINT tools built into Arkime

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





      


