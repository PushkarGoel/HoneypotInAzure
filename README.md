<h1> HoneypotInAzure </h1>

<h2>Description</h2>

This repo includes tutorial to setup AzureSentinel (SIEM) in azure. I then demonstrate how to create a honeypot in azure and setup log analytics to get logs of all the attacks being done on the machine. 
I also created alerts to get IPs which are performing brute force attack on the honeypot

<h2>Languages and Utilities Used</h2>
<h4> Languages: </h4>
- Powershell<br/>
<h4> Utilities: </h4>
- Azure Sentinel (SIEM)<br/>
- Microsoft Log Analytics <br/>

<h2>Environments Used</h2>

- Azure VMs

<h2> Lab Walkthrough</h2>

<p>
  1. I Logged into my Microsoft Azure Account. Then created a Resource group for this lab, named honeypotLab.
</p>

2. Then I created an azure VM which would act as my honeypot. For that, follow these steps <br/>
   2.1  Search Virtual Machine in azure and then click on Create > Azure Virtual Machine
   
   2.2  Then Select the Resource group as the one you created (honeypotlab in my case)
   
   2.3  Give name to VM. Change the zone ot the area you are in
   
   2.4 Change the Image to Windows machine as we are going to create RDP vulnerability in the vm
   
   2.5  Give  Username and Password of your own choice ( Tip: Make it same across resources so you do not forget it later on)
   
   2.6  Go to Networking tab. I created a new Network security group as I wanted to be no restrictions in the access for the VM ( so that its a honeypot!).

   
        Click on Advanced option for NIC network security group. Then click on Create new, and then add an inbound rule
   
        Then change the Destination port ranges to *. Priority should be something closer to 1000. I chose 1010.
   
        <img src="https://i.imgur.com/OVQR57G.png" height="80%" width="80%" alt="HONEYPOT LAB"/> <br/>

        Click on Add button. Then Go to Review + Create and the VM should be started

3. Then I created a log analytic workspace so that I could analyze the traffic of deployed vm. To do that, follow these steps:
   
   3.1.  Search Log analytics workspace and click on create

   3.2.  Set the Resource group the same as for vm. Give any name you like for the instance

   3.3.  Go to Review + Create and after verifying the details, click on create. A log analytics workspace should be succesfully created

4. Now I set up data collection rules, so that relevant information is stored in log analytics workspace. To do that follow these steps

   4.1. Search Microsoft defender for cloud. Go to Environment settings and select the log analytics workspace option
   
   4.2  Go to defender plans and set plan for servers to On ( SQL server can remain off as we dont need them for the lab)

   4.3  Go to data collection and set events as All Events
   
    
