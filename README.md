
<h1>SOC-Automation-Project</h1>



<h2>Description:</h2>
The "SOC Automation Project by Maunton Cyber" is a comprehensive home lab series designed to take viewers from the ground up in creating a fully functional Security Operations Center (SOC) process. The project focuses on integrating Security Orchestration, Automation, and Response (SOAR) tools, establishing effective case management with The Hive, and managing events using Wazuh. Through this project I have gained practical, hands-on experience in building, configuring, and troubleshooting SOC components, ultimately enhancing my cybersecurity operations skills.
<br>
<br>
<h2>Key learnings:</h2>
- Diagramming and Logical Planning: Creating a network diagram is a critical step in understanding the architecture of a SOC. This visual representation helps in mapping out data flow and understanding the components involved in the lab setup.
<br>
<br>
- Workflow Understanding: The step-by-step process of sending events, triggering alerts, and performing actions is crucial in security operations. Each component in the workflow has a specific role, from sending events to enriching Indicators of Compromise (IOCs).
<br>
<br>
<h2>Challenges faced:</h2>
- Error Management: Anticipating errors during the lab exercises is a part of the learning process. Errors can arise from incorrect configurations, misunderstanding of the tools, or logical errors in the setup.
<br>
<br>
- Complexity in Data Flow: Understanding how data flows between different components like Wazuh Manager, Shuffle, and The Hive can be complex. Ensuring the correct logical flow is a challenge that needs careful attention.
<br>
<br />


<h2>Project Stack:</h2>

- <b>Wazuh:<br>
-Role: Wazuh serves as the primary Security Information and Event Management (SIEM) tool in the stack. It collects, aggregates, and analyzes security events from various endpoints.<br>
-Functionality: Wazuh agents are installed on endpoints (e.g., Windows 10 client) to monitor and send security event data to the Wazuh Manager. The manager then processes these events, triggers alerts based on predefined rules, and sends them to other components in the stack for further action..</b>
- <b>Shuffle:<br>
  -Role: Shuffle is an open-source Security Orchestration, Automation, and Response (SOAR) platform that automates workflows within the SOC.<br>
  -Functionality: Upon receiving alerts from Wazuh, Shuffle can trigger automated actions such as enriching Indicators of Compromise (IOCs) by gathering additional data from open-source intelligence (OSINT) sources. Shuffle also forwards alerts to The Hive for case management and can send notifications to SOC analysts via email.</b>
- <b>The Hive:<br>
  -Role: The Hive is a case management system designed for SOCs. It allows for the organization, investigation, and resolution of security incidents.<br>
  -Functionality: Once Shuffle sends alerts to The Hive, they are logged as cases. SOC analysts can then investigate these cases, track the incident response process, and document their findings. The Hive integrates seamlessly with other tools in the stack to streamline the incident management workflow.</b>
- <b>Windows 10 Client:<br>
  -Role: This is the endpoint where the Wazuh agent is installed, representing a typical workstation in a network.<br>
  -Functionality: The Windows 10 client generates security events that are monitored by Wazuh. These events could include login attempts, application usage, or network traffic. The client is a critical source of data for the SOC.</b>
- <b>Internet/Cloud Services:<br>
  -Role: Provides the infrastructure where Wazuh Manager, The Hive, and Shuffle are hosted.<br>
  -Functionality: These services are hosted in the cloud, allowing for scalability and accessibility. The cloud setup ensures that the SOC components can interact with each other regardless of the physical location, enabling a robust and distributed SOC environment.</b>

<h1>Project walk-through:</h1>
  
<br />

<h3>SOC Automation Workflow Design:</h3>
This flowchart shows how security events are managed within an organization, covering everything from event collection and analysis to alerting, enrichment, and communication.<br>
<br>1. Windows 10 Client - Wazuh Agent (Send Events): This is an agent installed on a Windows 10 machine. It gathers security-related data like log entries, network activity, or system changes and sends this information to the Wazuh Manager.<br>
<br>2. Wazuh Manager (Receive Events): The Wazuh Manager acts as the central hub that receives and processes events from the agent. It aggregates, normalizes, and analyzes these events.<br>
<br>3. Send Alerts: The Wazuh Manager detects potential security threats by analyzing the events. If it finds any suspicious behavior, it generates alerts and sends them to Shuffle.<br>
<br>4. Enrich IOCs: "IOCs" stand for "Indicators of Compromise." In Shuffle, these IOCs are enriched by correlating the incoming data with information from threat intelligence platforms like VirusTotal.<br>
<br>5. Send Alert: After enrichment, the refined alerts are sent to TheHive for deeper investigation, collaboration, and case management.<br>
<br>6. Send Email: Simultaneously, alerts can be emailed to administrators, analysts, or other relevant parties to ensure they are aware of the security incidents in real-time.<br>
<br>7. SOC Analyst: The SOC Analyst, receives alerts from both TheHive and email. Their job is to analyze the incidents, respond to threats, and take the necessary actions.
<br />
<br />
<p align="center">
<img src="https://imgur.com/ClWhmJW.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>Setting up Windows 10 ISO on a virtual machine and installing Sysmon into Windows 10 VM:</h3>
In your browser, go to the download for Windows 10 and click the 'Download Now' for Create Windows installation media.
<br />
<br /> 
<p align="center">
<img src="https://imgur.com/dUpJovl.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />  
<p align="left">  
In the downloads folder, double click the Media Creation Tool that was just downloaded.
<br />
<p align="center">  
<img src="https://imgur.com/CblFwvN.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />  
<p align="left">
Choose Create Installation Media and click Next.
<br />
<p align="center">
<img src="https://imgur.com/1JNgSkN.png" height="80%" width="80%" alt="Project walk-through"/>
<br />  
<br />
<p align="left">
Choose ISO File and click next.
<p align="center">
<img src="https://imgur.com/RlWADPA.png" height="80%" width="80%" alt="Project walk-through"/>
<br /> 
<br />  
<p align="left">
In VirtualBox create a new Windows 10 machine from the ISO created. 
<br /> 
<p align="center">
<img src="https://imgur.com/jX7OwFe.png" height="80%" width="80%" alt="Project walk-through"/> 
<br />
<br />   
<p align="left">
  From a browser, download Sysmon from the Microsoft Sysmon Downloads.
<br /> 
<p align="center">
<img src="https://imgur.com/s0HeWDI.png" height="80%" width="80%" alt="Project walk-through"/>
<br /> 
<br />  
<p align="left">
Go to the Sysmon Config files from the Github repository(github.com/olafhartong/sysmon-modular) and choose 'sysmonconfig.xml'.
<br /> 
<p align="center">
<img src="https://imgur.com/2dR8zvD.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
Click 'Raw'.
<br />
<p align="center">
<img src="https://imgur.com/blOcNwg.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
Copy the text.
<p align="center">
<img src="https://imgur.com/ipslJyH.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
In the Downloads folder, 'extract all' from the Sysmon folder.
<p align="center">
<img src="https://imgur.com/XXoosdw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
Open the Sysmon file and place the Sysmon config file in there. 
<p align="center">
<img src="https://imgur.com/F7LDFY8.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Open up PowerShell and run as Administrator. 
<p align="center">
<img src="https://imgur.com/tzC090V.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Change Directories into the Downloads/Sysmon folder.<br />
Run the command to install Sysmon64.

  ## Command:
      .\Sysmon64.exe -i .\sysmonconfig.xml
<p align="center">
<img src="https://imgur.com/MTBXSDa.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>Setting up an instance in the cloud for Wazuh.</h3>
<br />
<p align="left">
Create an Ubuntu machine on the cloud for the Wazuh instance. I chose Digital Ocean where each intance is called a 'Droplet'.
<p align="center">
<img src="https://imgur.com/It6GY6l.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Create a firewall on the 'Network' tab.
<p align="center">
<img src="https://imgur.com/ggYf1dk.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Create two Inbound rules using your home routers Public IP address. 
<p align="center">
<img src="https://imgur.com/nOvxMiJ.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Create the three Outbound rules and click 'Create Firewall'.
<p align="center">
<img src="https://imgur.com/kWExugW.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
To add the Firewall to the droplet navigate back to 'Droplets' and select the newly created one.
<p align="center">
<img src="https://imgur.com/OHPvQ0L.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Select the 'Networks" tab.
<p align="center">
<img src="https://imgur.com/og1FTMB.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Scroll down and select the Firewalls 'Edit' tab.
<p align="center">
<img src="https://imgur.com/fM3vsJr.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Select the newly created Firewall.
<p align="center">
<img src="https://imgur.com/53DoDe7.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
Select the Droplets tab and click 'Add Droplets'.
<p align="center">
<img src="https://imgur.com/lhp1Htg.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Select the Droplet and click 'Add Droplet'.
<p align="center">
<img src="https://imgur.com/kguHBSj.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
To start your Ubuntu(Wazuh) instance, select the 'Launch Droplet Console'.
<p align="center">
<img src="https://imgur.com/uc4ZDx9.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
In the console, run the commands to update and upgrade Ubuntu.

  ## Command:
    apt-get update && apt-get upgrade -y 
<p align="center">
<img src="https://imgur.com/Yivu48w.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>Wazuh install on the Ubuntu machine</h3>
In the console, run the commands to install Wazuh.

  ## Command:
    curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
<p align="center">
<img src="https://imgur.com/IHhoYBN.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Save the user name and password provided after the install in order for access to Wazuh .
<p align="center">
<img src="https://imgur.com/xHoyYnw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Copy the IP address of the Wazuh(Ubuntu) droplet for access to Wazuh.
<p align="center">
<img src="https://imgur.com/tYVIorw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Open a new browser tab and paste the IP address of the Wazuh(Ubuntu) droplet.<br>
The browser may restrict access so use proceed option.
<p align="center">
<img src="https://imgur.com/mWTOsXW.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />  
<p align="left">
Enter the credentials that were provided after the install of Wazuh.
<p align="center">
<img src="https://imgur.com/fZGXLlw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
After login you will be presented with the Wazuh dashboard.
<p align="center">
<img src="https://imgur.com/IyPwyrR.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<h3>Setting up TheHive on an Ubuntu machine from the cloud(DigitalOcean).</h3>
<p align="left">
Setup another Ubuntu instance, add the Firewall as was done with the Ubuntu(Wazuh) droplet, and launch the console.
<p align="center">
<img src="https://imgur.com/6zVfOfY.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
From the console use nano to edit the cassandra.yaml file.
  
 ## Command:
    nano /etc/cassandra/cassandra.yaml  
<p align="center">
<img src="https://imgur.com/43iJA6R.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<p align="left">
Edit the following...and save the file.
<p align="center">
<img src="https://imgur.com/PQC6uIl.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://imgur.com/F3oyKlw.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://imgur.com/plwJolm.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://imgur.com/q176CQM.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Stop the service for cassandra, remove files from /var/lic/cassandra/*, start cassandra.service, and check the status for active to know it is running.
  
 ## Command:
    systemctl stop cassandra.service
    rm -rf /var/lic/cassandra/*
    systemctl start cassandra.service
    systemctl status cassandra.service
<p align="center">
<img src="https://imgur.com/JZAuWMr.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />   
<p align="left">
Edit the following in the file for elasticsearch using nano.
  
 ## Command:
    nano /etc/elasticsearch/elasticsearch.yml
<p align="center">
<img src="https://imgur.com/R4pUu4y.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<img src="https://imgur.com/MVRob6R.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<img src="https://imgur.com/I2qjauS.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<img src="https://imgur.com/do2ablD.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
Run the following commands to start, enable and check the status of elasticsearch.
  
 ## Command:
    systemctl start elasticsearch
    systemctl enable elasticsearch
    systemctl status elasticsearch
<p align="center">
<img src="https://i.postimg.cc/8Cfy4wk8/23.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Run the following commands to check the ownership of /opt/thp files, and change owner to thehive.
  
 ## Command:
    ls -la /opt/thp
    chown -R thehive:thehive /opt/thp
<p align="center">
<img src="https://i.postimg.cc/7hrYhBhq/24.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
Run the following commands to edit the application/conf file for thehive and configure as shown.
  
 ## Command:
    nano /etc/thehive/application.conf
<p align="center">
<img src="https://i.postimg.cc/4ywkGwhL/25.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<img src="https://i.postimg.cc/nz00cW0D/26.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<img src="https://i.postimg.cc/QMDbgDz7/27.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<img src="https://i.postimg.cc/SRHLnb8J/28.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Run the following commands to start, enable, and check status of thehive.
  
 ## Command:
    systemctl start thehive
    systemctl enable thehive
    systemctl status thehive
<p align="center">
<img src="https://i.postimg.cc/d11GnVjh/29.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Open a new browser and paste the IP address of thehive(Ubuntu) at port 9000. The default username and password are:
  
 ## Username and Password:
    admin@thehive.local
    secret 
<p align="center">
<img src="https://i.postimg.cc/3x08j5G3/30.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://i.postimg.cc/j5MY0Zf8/31.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<h3>Deploying a Wazuh agent into Windows 10</h3>
<p align="left">
To find out what all the username and passwords are run the following commands:
  
 ## Username and Password:
    ls
    tar -xvf wazuh-install-files.tar
    cd wazuh-install-files/
    ls
    cat wazuh-passwords.txt
    
<p align="center">
<img src="https://i.postimg.cc/dVJM1b9W/1.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
On the Wazuh dashboard click the 'Add agent'.
<p align="center">
<img src="https://i.postimg.cc/ZKFg1fh6/3.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
Choose the Windows version for the Windows 10 VM Client.
<p align="center">
<img src="https://i.postimg.cc/VN1NzZS1/4.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
The assigned server address will be the IP of the Wazuh(Ubuntu). Create an assigned agent name.
<p align="center">
<img src="https://i.postimg.cc/vm3GbYFL/5.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
Copy these commands and run them in Windows 10 PowerShell.
<p align="center">
<img src="https://i.postimg.cc/wvnMYqL4/6.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://i.postimg.cc/65r3FN3z/7.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://i.postimg.cc/1zt3gnKY/9.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br /> 
<p align="left">
Check 'Services' in Windows and the Wazuh dashboard to see Wazuh running and agent successfully added.
<p align="center">
<img src="https://i.postimg.cc/WzSyJ38X/10.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br /> 
<img src="https://i.postimg.cc/QxxwZQNP/11.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />   
  
  
  
  







  
</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
