# Cisco-Umbrella-App-For-Splunk

Got Cisco Umbrella data in Splunk and annoyed that Cisco didn't build an app to show Dashboard and Reports in Splunk?  
Here is a simple, but powerful Splunk app for Umbrella.  

There are a few options to get Umbrella data into Splunk:
1. Cisco-managed AWS S3  <- Preferred Method
2. Customer-managed AWS S3

**Data Flow**

![Splunk Umbrella Data Flow S3](https://user-images.githubusercontent.com/20860518/120950530-f80ff200-c714-11eb-8ec7-aac6fa28f1af.png)


# Prerequisites:

**Splunk Enterprise Customers**

*Heavy Forwarder*

1. Linux Server OS (Cisco Requirement)
2. aws-cli installed in Linux
3. Splunk Enterprise >=7.x
4. Cisco Umbrella Add-on for Splunk (https://splunkbase.splunk.com/app/3926/)
  - Contains Linux Bash Scripts to pull data from S3 to a flat file log in Splunk
  - Follow instructions of this Add-on to get data into Splunk Enterprise
5. \>50GB of Storage on Heavy Forwarder
  - Depending upon Linux file system type and settings and volume of DNS traffic from Umbrella, local storage can fill up.
  - You can edit the included bash scripts in the Add-on to be more aggressive with deleting old flat file log data.
  - If you're a Linux expert or have advanced knowledge, I suggest ZFS or BTFS for the file system and enable compression to save on storage.


*Indexer*

1. Create new index with any name or use an existing one
2. Splunk Enteprise >=7.x

*Search Head*

1. Cisco Umbrella Add-on for Splunk (https://splunkbase.splunk.com/app/3926/)
2. Cisco Umbrella App (this app)
3. Sankey Diagram Visualization: (https://splunkbase.splunk.com/app/3112/)
4. (Optional, but highly recommended): Common Information Model (CIM) App (https://splunkbase.splunk.com/app/1621/)


**Splunk Cloud Customers**
1. Splunk Cloud IDM or on-prem Splunk Heavy Forwarder (see notes above for Heavy Forwarder)
2. Cisco Umbrella Add-on for Splunk (https://splunkbase.splunk.com/app/3926/) installed on IDM and Splunk Cloud; may require Cloud Support Ticket for installation on both IDM and Splunk Cloud instance.
3. Cisco Umbrella App (this app), use Custom App upload function in Splunk Cloud
4. Sankey Diagram Visualization: (https://splunkbase.splunk.com/app/3112/)
5. (Optional, but highly recommended): Common Information Model (CIM) App (https://splunkbase.splunk.com/app/1621/)
6. Create new index with any name or use an existing one

# Cisco Umbrella App for Splunk Entperise Instructions
1. Install this app on your Search Head - Apps -> Manage Apps -> Install App from File
2. Open the App 
3. Settings -> Advanced Search -> Search Macros -> umbrella_index
4. Edit the macro with the appropriate index name -> Save
5. Open the App
6. (Optional Step - CIM Data Model) - add Umbrella index name to "Network Resolution" Data Model and accelerate it

# Screenshots

![image](https://user-images.githubusercontent.com/20860518/120951777-99984300-c717-11eb-8e10-bce77448d3fe.png)

![image](https://user-images.githubusercontent.com/20860518/120951822-b59be480-c717-11eb-8204-5664551744eb.png)

![image](https://user-images.githubusercontent.com/20860518/120951948-03b0e800-c718-11eb-8805-7c7a3a561dc4.png)

![image](https://user-images.githubusercontent.com/20860518/120952435-06600d00-c719-11eb-930f-d25f5795b391.png)



