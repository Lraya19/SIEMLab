<h1>SIEM - Using Azure Sentinel to Map Cyber Attacks</h1>


<h2>Description</h2>
Project consists of using Security Information and Event Management tools to collect and analyze cyber attack data from all over the world. We will create a Virtual Machine using an Azure subscription, turn external firewall off for that VM, and turn Windows firewall off so that it’s really exposed to the internet. We are creating a honeypot so it can be discovered quickly by attackers. We'll create a map for attacker data to visualize as well as analyze attack location information. Lastly, we'll use PowerShell to extract the IP address from the Windows log and send it to a third-party API. The API will derive the coordinates and send it back to our VM which we will then use to create a custom log with geographic data on it.
<br />


<h2>Languages and Utilities Used</h2>
 
- <b>Azure Sentinel</b>
- <b>Azure Virtual Machine</b>
- <b>PowerShell Script</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Create a Virtual Machine on Azure: 
 <br/> The goal is to make the VM very discoverable so that people start attacking it. Normally we wouldn’t want to do this, but for the purpose of our lab we are making it enticing and discoverable to people so that we use SIEM tools to analyze our data.
<img src="https://i.imgur.com/2kbi9x9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 
<br />
Next we create a new resource group. This is a logical grouping of resources on Azure that usually share the same lifespan. Everything in this lab will be put in this resource group.:
 <br/>
<img src="https://i.imgur.com/z97JIRD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open Log Analytics Workspaces (LAW): The purpose for creating a new LAW is to ingest logs into our VM. We will ingest the Windows Event Logs and create our own custom log that contains geographic information to discover where these attacks are coming from. Our SIEM will connect to this workspace to display the geodata on the map. <br/>
<img src="https://i.imgur.com/6dnyAMU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Connect VM to our workspace:  <br/>
<img src="https://i.imgur.com/px80Q1u.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set up Azure Sentinel:  <br/>
<img src="https://i.imgur.com/qizXDLl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />Nessus can be configured to schedule regular scans and monitor the network continuously, ensuring that any new vulnerabilities are promptly identified and addressed.

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
