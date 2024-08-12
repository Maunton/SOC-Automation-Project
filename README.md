 <h1>$${\color{yellow}SOC \space Automation \space Project}$$</h1>


<h2>$${\color{blue}Description:}$$</h2>
The "SOC Automation Project by Maunton Cyber" is a comprehensive home lab series designed to take viewers from the ground up in creating a fully functional Security Operations Center (SOC) process. The project focuses on integrating Security Orchestration, Automation, and Response (SOAR) tools, establishing effective case management with The Hive, and managing events using Wazuh. Through this project I have gained practical, hands-on experience in building, configuring, and troubleshooting SOC components, ultimately enhancing my cybersecurity operations skills.
<br>
<br>
<h2>$${\color{blue}Key \space Learnings:}$$</h2>
- Diagramming and Logical Planning: Creating a network diagram is a critical step in understanding the architecture of a SOC. This visual representation helps in mapping out data flow and understanding the components involved in the lab setup.
<br>
<br>
- Workflow Understanding: The step-by-step process of sending events, triggering alerts, and performing actions is crucial in security operations. Each component in the workflow has a specific role, from sending events to enriching Indicators of Compromise (IOCs).
<br>
<br>
<h2>$${\color{blue}Challenges \space Faced:}$$</h2>
- Error Management: Anticipating errors during the lab exercises is a part of the learning process. Errors can arise from incorrect configurations, misunderstanding of the tools, or logical errors in the setup.
<br>
<br>
- Complexity in Data Flow: Understanding how data flows between different components like Wazuh Manager, Shuffle, and The Hive can be complex. Ensuring the correct logical flow is a challenge that needs careful attention.
<br>
<br />


<h2>$${\color{blue}Project \space Stack:}$$</h2>

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

<h1>$${\color{yellow}Project \space Walk-through:}$$</h1>
  
<br />

<h2>$${\color{blue}SOC \space Automation \space Workflow \space Design:}$$</h2>
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
<h3>$${\color{blue}Setting \space up \space Windows \space 10 \space ISO \space on \space a \space virtual \space machine \space and \space installing \space Sysmon \space in \space the \space Windows \space VM:}$$</h3>
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

  ## $${\color{red}Command:}$$
      .\Sysmon64.exe -i .\sysmonconfig.xml
<p align="center">
<img src="https://imgur.com/MTBXSDa.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>$${\color{blue}Setting \space up \space an \space instance(Droplet) \space in \space the \space cloud \space for \space Wazuh:}$$</h3>
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

  ## $${\color{red}Command:}$$
    apt-get update && apt-get upgrade -y 
<p align="center">
<img src="https://imgur.com/Yivu48w.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>$${\color{blue}Wazuh \space install \space on \space the \space Ubuntu \space machine:}$$</h3>
In the console, run the commands to install Wazuh.

  ## $${\color{red}Command:}$$
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
<h3>$${\color{blue}Setting \space up \space TheHive \space on \space an \space Ubuntu \space machine \space from \space the \space cloud(DigitalOcean):}$$</h3>
<p align="left">
Setup another Ubuntu instance, add the Firewall as was done with the Ubuntu(Wazuh) droplet, and launch the console.
<p align="center">
<img src="https://imgur.com/6zVfOfY.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br /> 
<p align="left">
From the console use nano to edit the cassandra.yaml file.
  
 ## $${\color{red}Command:}$$
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
  
 ## $${\color{red}Command:}$$
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
  
 ## $${\color{red}Command:}$$
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
  
 ## $${\color{red}Command:}$$
    systemctl start elasticsearch
    systemctl enable elasticsearch
    systemctl status elasticsearch
<p align="center">
<img src="https://i.postimg.cc/8Cfy4wk8/23.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Run the following commands to check the ownership of /opt/thp files, and change owner to thehive.
  
 ## $${\color{red}Command:}$$
    ls -la /opt/thp
    chown -R thehive:thehive /opt/thp
<p align="center">
<img src="https://i.postimg.cc/7hrYhBhq/24.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
Run the following commands to edit the application/conf file for thehive and configure as shown.
  
 ## $${\color{red}Command:}$$
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
  
 ## $${\color{red}Command:}$$
    systemctl start thehive
    systemctl enable thehive
    systemctl status thehive
<p align="center">
<img src="https://i.postimg.cc/d11GnVjh/29.png" height="80%" width="80%" alt="Project walk-through"/>  
<br />
<br />
<p align="left">
Open a new browser and paste the IP address of thehive(Ubuntu) at port 9000. The default username and password are:
  
 ## $${\color{red}Usernames \space and \space Passwords:}$$
    admin@thehive.local
    secret 
<p align="center">
<img src="https://i.postimg.cc/3x08j5G3/30.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<img src="https://i.postimg.cc/j5MY0Zf8/31.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<h3>$${\color{blue}Deploying \space a \space Wazuh \space agent \space from \space Windows \space client:}$$</h3>
<p align="left">
To find out what all the username and passwords are run the following commands:
  
 ## $${\color{red}Command:}$$
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
<p align="left">
<h3>$${\color{blue}Setting \space up \space Windows \space client \space telementary:}$$</h3>  
Locate in Windows 10 client the ossec.conf file and copy it into the same directory making it a backup.
<p align="left">

  
## $${\color{red}File \space path:}$$
    C:\Program Files (x86)\ossec-agent
<p align="center">
<img src="https://imgur.com/xmYm8CL.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />   
<p align="left">
Open the ossec.conf file with Notepad and run as administrator.
<p align="center">
<img src="https://imgur.com/11bavc3.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br /> 
<p align="left">
In Windows 10 open the Event Viewer. Click Applications and Services Logs in the drop down.
<p align="center">
<img src="https://imgur.com/Y6MkGqu.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
Click the Sysmon directory.
<p align="center">  
<img src="https://imgur.com/BfhYFqv.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
Right click Operational and click Properties.
<p align="center">   
<img src="https://imgur.com/PlCOqkj.png" height="80%" width="80%" alt="Project walk-through"/>
  <br />
  <br />
<p align="left">
Copy the Full Name- 'Microsoft-Windows-Sysmon/Operational'.
<p align="center"> 
<img src="https://imgur.com/4e966WC.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br /> 
<p align="left">
Paste 'Microsoft-Windows-Sysmon/Operational' into the ossec.conf file and replacing application at location.
<p align="center"> 
<img src="https://imgur.com/wcFD0GE.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br /> 
<p align="left">
Modify the ossec.conf file as shown...and save.
<p align="center"> 
<img src="https://imgur.com/7aUR92P.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Open the Windows Services and restart Wazuh.
<p align="center"> 
<img src="https://imgur.com/dWJqqIa.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br /> 
<p align="left">  
<h3>$${\color{blue}Setup \space ossec.conf \space and \space Filebeat \space in \space Wazuh:}$$</h3>
Open Wazuh(Ubuntu) console and run the following commands to copy the ossec.conf as a backup. Run the following command to open a nano text editor to configure the ossec.conf file.
  
## $${\color{red}Command:}$$
    cp /var/ossec/etc/ossec.conf ~/ossec-backup.conf
    nano /var/ossec/etc/ossec.conf
<p align="center"> 
<img src="https://imgur.com/ziVL4Kp.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />   
<p align="left">
Modify the ossec.conf file as shown...and save.
<p align="center"> 
<img src="https://imgur.com/bR49jRZ.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Change directories and open filebeat.yml with nano.

## $${\color{red}Command:}$$
    cd /var/ossec/logs/archives/
    nano /etc/filebeat/filebeat.yml  
<p align="center"> 
<img src="https://imgur.com/4kQF1q7.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Modify the filebeat.yml file as shown...and save.
<p align="center"> 
<img src="https://imgur.com/TD8pgOB.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br /> 
<p align="left">
Restart filebeat.

## $${\color{red}Command:}$$
    systemctl restart filebeat 
<p align="center"> 
<img src="https://imgur.com/kL5aaoZ.png" height="80%" width="80%" alt="Project walk-through"/>  
  <br />
  <br />
<p align="left">  
<h3>$${\color{blue}Install \space and \space Setup \space Mimikatz \space in \space Windows \space client}$$</h3>
Open a browser in the Windows client machine and go to the Mimikatz github page. Download the mimikatz_trunk.zip file.

## $${\color{red}Link:}$$
    https://github.com/gentilkiwi/mimikatz/releases/tag/2.2.0-20220919
<p align="center"> 
<img src="https://imgur.com/0FVq0KZ.png" height="80%" width="80%" alt="Project walk-through"/>  
  <br />
  <br />
<p align="left">
In the downloads folder, extract the contents of the Mimikatz_trunk file.
<p align="center"> 
<img src="https://imgur.com/iacgmwu.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br /> 
<p align="left">
Copy the file path for Mimikatz x64 version.
<p align="center"> 
<img src="https://imgur.com/LR6fIrD.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Open PowerShell, run as administrator, and change directories to \Downloads\mimikatz_trunk\x64.
<p align="center"> 
<img src="https://imgur.com/iGPOq7U.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">  
Use the following command to run Mimikatz...

## $${\color{red}Command:}$$
    .\mimikatz.exe
<p align="center"> 
<img src="https://imgur.com/o4vRCNd.png" height="80%" width="80%" alt="Project walk-through"/>  
  <br />
  <br />
<p align="left">  
<h3>$${\color{blue}Setup \space an \space Index \space pattern \space on \space Wazuh \space dashboard \space to \space capture \space Mimikats \space on \space   Windows \space client:}$$</h3>
Open Wazuh dashboard, select 'Dashboard Management', select 'Index patterns', and select 'Create index pattern'.
  <br />
  <br />
<p align="center"> 
<img src="https://imgur.com/83vHJj7.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Name the Index pattern as 'wazuh-archives-**' and click 'next step'.
<p align="center"> 
<img src="https://imgur.com/e2wpcvq.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Select 'timestamp' and click 'Create index pattern'.
<p align="center"> 
<img src="https://imgur.com/Btf58RW.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
On the Windows PowerShell run Mimikatz again.
<p align="center"> 
<img src="https://imgur.com/DEjTPQR.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
On the Wazuh dashboard go to 'Discover' to view new alerts.
<p align="center"> 
<img src="https://imgur.com/NhhEvKg.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Select wazuh-archives-**, mimikatz, refresh, and select the first Timestamp.
<p align="center"> 
<img src="https://imgur.com/P46XxlA.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Inside the 'Document Details' there is important information regarding the new alert from the Windows client regarding mimikatz.
<p align="center"> 
<img src="https://imgur.com/jZKJOGa.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
<h3>$${\color{blue}Wazuh \space rules \space creation:}$$</h3>
In Wazuh go to Management-Rules and click 'Manage rules files'.
  <br />
  <br />
<p align="center"> 
<img src="https://imgur.com/weF15SY.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />  
<p align="left">
Type 'sysmon' to find a similar rule with an id_1 and then select the sysmon rule with id_1.
<p align="center"> 
<img src="https://imgur.com/9ZDuv3t.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Copy one of these rules to build out a custom rule for mimikatz.
<p align="center"> 
<img src="https://imgur.com/gBjYs9g.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Go back to rules and click 'Custom rules'.
<p align="center"> 
<img src="https://imgur.com/iDu8Lb3.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Click the pencil icon to edit the new custom rule.
<p align="center"> 
<img src="https://imgur.com/izjXdL6.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Go down to the last rule and this is where we will paste our rule we copied.
<p align="center"> 
<img src="https://imgur.com/ylkheXk.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Modify the rule: change the rule id, change the field name, description, mitre id, and click 'Save'.
<p align="center"> 
<img src="https://imgur.com/4sMLK3j.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Click 'Restart'.
<p align="center"> 
<img src="https://imgur.com/2a2xz5w.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Now that we made a rule to be alerted from mimikatz usage, we will change the executable name to something else.
<p align="center"> 
<img src="https://imgur.com/vxILVF4.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<img src="https://imgur.com/1rj8zJh.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left">
Rerun mimikatz as the new name change.
<p align="center"> 
<img src="https://imgur.com/oMTDnLD.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
View the Document Details for the new timestamp. The timestamp alerted of mimikatz usage even with the name changed.
<p align="center"> 
<img src="https://imgur.com/sx5COCv.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
<h3>$${\color{blue}Setup \space Shuffle:}$$</h3>
Open Shuffler.io on a new browser and create a new account. Click 'Workflows'.
  <br />
  <br />
<p align="center"> 
<img src="https://imgur.com/zE61a1c.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Click 'New Workflow".
<p align="center"> 
<img src="https://imgur.com/qn7J4Xb.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Name the project, enter Usecase, put a description, and Save Changes.
<p align="center"> 
<img src="https://imgur.com/HdgOtXj.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
The initial workflow space is now open. This where Apps and Triggers will be added.
<p align="center"> 
<img src="https://imgur.com/BZY7YkH.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Select 'Triggers' and drag 'Webhooks' over to the workspace. Click on Webhooks, rename it and copy the webhook URI.
<p align="center"> 
<img src="https://imgur.com/063Ksvo.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Click 'Change Me'. Find actions is Repeat back to me. Call is $exec.
<p align="center"> 
<img src="https://imgur.com/Tvx7IWx.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
In the Wazuh console open the /var/ossec/etc/ossec.conf file with nano.

 ## $${\color{red}Command:}$$
    nano /var/ossec/etc/ossec.conf 
<p align="center"> 
<img src="https://imgur.com/cRcADOJ.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Inside of the ossec.conf file paste the Webhook URI. Save the file.
<p align="center"> 
<img src="https://imgur.com/2QaaQ83.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
<p align="left"> 
Restart wazuh-manager.service. Check the status.

 ## $${\color{red}Command:}$$
    sysytemctl restart wazuh-manager.service 
    sysytemctl status wazuh-manager.service
<p align="center"> 
<img src="https://imgur.com/dWG5b2D.png" height="80%" width="80%" alt="Project walk-through"/> 
  <br />
  <br />
























  
</p>


<!--
 ```diff
<!
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
