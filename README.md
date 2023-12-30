# Azure Sentinel: Real-Time Threat Detection and Global Geospatial Analysis

<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/Blue%20Minimalist%20Profesional%20Personal%20Linkedln%20Banner.png?raw=true" >

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
<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/Sentinerl%20visual.jpg?raw=true"  width="30%">
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
<p>In the initial phase of the project, a pivotal step was the creation of a Windows Virtual Machine (VM) specifically designed to act as a honeypot. The honeypot is strategically configured with Remote Desktop Protocol (RDP) enabled, attracting potential attackers and serving as a controlled environment for security monitoring</p>

<img src="https://github.com/bayulus/azure-honeynet-livetraffic/blob/main/images/1.PNG?raw=true" > 

  


