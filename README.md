# Azure Sentinel: Real-Time Threat Detection + SOC + Honeynet
<br>

<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/soc.png?raw=true" >

<p> This project covers the end-to-end setup of Azure Sentinel, a Security Information and Event Management (SIEM) solution. It includes connecting it to a live virtual machine acting as a honeypot to observe and analyze RDP brute force attacks worldwide. The custom PowerShell script enhances the analysis by looking up attackers' geolocation information and visualizing it on the Azure Sentinel Map.</p>

<h2>Here's A High-Level Outline of The Steps I Took For This Project 💫</h2>

  - **Step 1:** I set up an Azure Sentinel workspace to collect and analyze security data.
  - **Step 2:** Deployed a virtual machine to act as a honeypot. Ensure it has RDP (Remote Desktop Protocol) enabled to attract potential attackers.
  - **Step 3:** Configure Azure Sentinel to collect data from my honeypot VM. Integrate other relevant data sources for a comprehensive security overview.
  - **Step 4:** Define security rules in Azure Sentinel to identify potential RDP brute force attacks and configure alerts based on specific security events.
  - **Step 5:** I created a custom PowerShell script to enhance analysis. Use IP geolocation services **(ipgeolocation.io)** to look up attackers' locations based on IP addresses. Extract relevant information such as country, city, and coordinates.
  - **Step 6:** Integrate the geolocation data into Azure Sentinel. Configured the Azure Sentinel Map to display the attackers' locations by visualizing it on the map.
  - **Step 7:** I establish procedures for responding to security incidents and determine appropriate actions based on the severity of the detected threats.

<p align="center">
<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/core-senti.png?raw=true"  width="70%">
</p>

<p>Azure Sentinel follows a security operations model that consists of four main phases: Collect, Detect, Investigate, and Respond. These phases are designed to provide a systematic approach to managing and responding to security incidents.</p>

  - **Collect:** In this phase, the focus is on collecting data from various sources, including logs, events, and telemetry data. Azure Sentinel supports a wide range of connectors and integrations to collect data from different platforms and services. Data is ingested into the Azure Sentinel workspace, where it is stored and made available for analysis. **<i>In this case, I am collecting data from a Virtual Machine</i>**.
    
  - **Detect:** In the detection phase, security rules are applied to the collected data to identify potential security incidents.
These rules define patterns and conditions that, when met, trigger alerts. When a potential security incident is detected, an incident is created, and relevant information is associated with it.

  - **Investigate:** Immediately an Incident is detected, this phase comes u. I use Azure Sentinel's investigation tools to explore and analyze incidents.
Correlation of data from various sources helps build a comprehensive understanding of the incident.

  - **Automate:** In the response phase, I take action to mitigate and remediate security incidents. Responses can be automated using playbooks or executed manually based on the severity of the incident.

# Implementation

<h2>1. Creating a Virtual Machine</h2>
<p>In the initial phase of the project, a pivotal step was the creation of a Windows Virtual Machine (VM) specifically designed to act as a honeypot. The honeypot is strategically configured with Remote Desktop Protocol (RDP) enabled, attracting potential attackers and serving as a controlled environment for security monitoring</p><img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/1.PNG?raw=true" > 

<h2>2. Creating a Log Analytics Workspace and Adding the Virtual Machine</h2>
<p>As part of the Azure Sentinel setup, a crucial step involved the creation of a Log Analytics workspace. This workspace serves as the central repository for collecting, storing, and analyzing log data generated by various resources, including the honeypot virtual machine.</p>
<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/2.PNG?raw=true" > 

With the Log Analytics workspace successfully configured and connected to the honeypot VM, the project is poised to advance to subsequent phases. The focus now shifts towards fine-tuning detection rules, exploring analytics queries, and leveraging the integrated data for a comprehensive security overview within Azure Sentinel.

<h2>3. PowerShell Script Integration for Geolocation Enrichment</h2>
<p>In general, this PowerShell script is designed to enhance the analysis of failed RDP events by collecting and enriching data with geolocation information. It continuously monitors the Windows Event Viewer, extracts relevant details from failed RDP events, performs IP geolocation lookups, and updates a custom log file. The script's output, including geolocation data, provides valuable insights into the origin of potential security threats. <b></b>When integrated into Azure Sentinel through Log Analytics workspace tables, this enriched data contributes to more effective threat detection and response capabilities</b> </p>

<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/8.PNG?raw=true" >

<h2>4. Azure Sentinel Integration and Workbook Query</h2>
<p>This step involved the seamless integration of Azure Sentinel with the existing Log Analytics workspace, creating a unified environment for security monitoring. Leveraging the same workspace ensures a cohesive approach to data analysis and incident response. A custom workbook query, named <b>HoneyPot Failed RDP MAP</b>, was introduced to transform and enrich raw data for enhanced analysis within Azure Sentinel. The integration sets the stage for advanced security analysis within Azure Sentinel. The workbook query extracts critical information, creating a structured dataset for in-depth analysis. Future steps may include rule configuration, visualizations, and response playbooks to fortify the project's security posture in the Azure Sentinel environment.</p>

<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/3.PNG?raw=true" >

<h2>5. Observation of Brute Force Attacks and Anomalous Activities</h2>
<p>Following the successful integration of Azure Sentinel and the completion of the entire setup, a crucial phase involved actively monitoring the environment for security events. After patiently waiting for approximately three hours, the system began to detect and log instances of brute force attacks originating from diverse locations.</p>

  - <h3>Visualization of Attack Maps Before Hardening Security/Controls</h3>
  <img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/9.PNG?raw=true">
         <p>After three hours of system monitoring, notable attack activities were detected, originating from the following locations and IP addresses: Netherlands - 116.130.215.81 & Taiwan - 60.249.86.48</p>

   - <h3>Visualization of Attack Maps After Hardening Security/Controls</h3>
   <img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/7.PNG?raw=true">

  - <h3>Query Result of Failed RDP Events Showing Attack Metrics</h3>
  <p>The query result below also reveals a compilation of usernames utilized by attackers attempting to log in, indicative of a potential brute-force attack. This consolidated view provides insights into the patterns and intensity of the login attempts, aiding in the identification and understanding of the ongoing security threat.</p>
  <img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/rename.PNG?raw=true" >

  - <h3>IP Address Lookups on The Attackers' IP</h3>
  <p>I conducted IP address lookups on the attackers' IP addresses using AbuseIPDB for further investigation and analysis</p>
  <img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/10.PNG?raw=true" >


  - <h3>Security Incident Event and Alert</h3>
  <img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/6.PNG?raw=true" >


# Conclusion
<p>In this project, a small network was set up in Microsoft Azure to simulate a honeynet. Different sources of logs were connected to a Log Analytics workspace. To monitor and respond to security threats, Microsoft Sentinel was used to detect unusual activity and create incidents based on the collected logs.

Before applying any security measures, metrics were recorded in the insecure environment. Then, security controls were implemented, and metrics were measured again to see the impact of these measures. It was found that the number of security events and incidents reduced significantly after implementing the security controls, showing their effectiveness in protecting the network.

However, it is important to consider that if the resources within the network were heavily used by regular users during this 24-hour period after implementing security controls, there might have been more security events and alerts generated. This is because normal user activities can sometimes trigger false positives or be mistaken for malicious behavior.</p>
  
  

  

     
     
     
   



  


