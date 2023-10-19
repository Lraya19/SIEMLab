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
 <br/> We are creating a honeypot so that it's enticing and discoverable to people. We'll use SIEM tools to analyze our data.
<img src="https://i.imgur.com/2kbi9x9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 
<br />
Next we create a new resource group. This is a logical grouping of resources on Azure that usually share the same lifespan. Everything in this lab will be put in this resource group:
 <br/>
<img src="https://i.imgur.com/z97JIRD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next we'll open Log Analytics Workspaces (LAW): The purpose for creating a new LAW is to ingest logs into our VM. We will ingest the Windows Event Logs and create our own custom log that contains geographic information to discover where these attacks are coming from. Our SIEM will connect to this workspace to display the geodata on the map. <br/>
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
<br />
API using ipgeolocation website + Run PowerShell script:  <br/>
 Using the ipgeolocation website, we are able to use the API to return location information. We will use this information to create our own custom log and send that log to analytics workspace. We will use Sentinel to read the latitude and longitude and then plot this on our map. By running the PowerShell script we are able to get our geodata from attackers. 
<p align="center">
 After some time, our honeypot is under attack. We can observe how people from all over the world are trying to brute force their way in. <br/>
<img src="https://i.imgur.com/kqUk3tp.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center">
Next, we'll create custom logs in order to train log analytics for what to look for in the attacks logs when extracting data. <br/>
<img src="https://i.imgur.com/JN3LciJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="center">
Example field extraction: <br/>
<img src="https://i.imgur.com/0XRUH5v.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
All custom fields for log extraction: <br/>
<img src="https://i.imgur.com/hMLXNQh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Next we'll create a new workbook in Sentinel. We must wait a few moments to see how discoverable our honeypot has become. As this is happening, our query will continue to run on Sentinel and populating our map with attacks: <br/>
<img src="https://i.imgur.com/pe1QrSu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Our honeypot has attracted many attackers. Here we see the logs our custom fields have created for each potential threat: <br/>
<img src="https://i.imgur.com/jU8Eg1f.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Attack map after 5 hours:  <br/>
 Our SIEM tool has automatically created a map with data representing geolocations for each attack!
<img src="https://i.imgur.com/OiZydu1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 <p align="center">
Attack map after 10 hours:  <br/>
 As our VM continues to be online, Sentinel will continue populating this map with new attackers. 
<img src="https://i.imgur.com/nNfHxV0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

 <p align="center">
Key Takeaways!  <br/>
  
  - As soon as any of your devices connect to the internet they are exposed to people from all around the world who will be able to discover and potentially try to gain access to your devices in some way.

    
  - Make sure you have strong password habits. Most failed log on attempts captured in our logs shows how brute force attacks may help an attacker gain access simply because the password wasn’t strong enough to 
    keep them out.

    
  - Cybersecurity analysts may use technology such as Azure Sentinel to help aid their security for their organizations in the same manner! By staying up to date on the latest security tools we can help fortify a strong security posture for your organization and keep its integrity intact.

    
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
