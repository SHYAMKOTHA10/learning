# Google Load Balancer Integration units:
## Introduction:
    Cisco Cloud Center (version 5.0 and later) extends its support with Google Load Balancer (LB) through this Integration Unit (IU) for setup,start and stop. This LB Google IU leverage Google REST APIs to create and delete LBs dynamically.
# Service Installation:
    login to CloudCenter as an administrator and click on Admin--> Services --> Add service
    
    Service Type: External Service
    
    Service logo: Downlad logo from : <location of logo path>
    
    Name: Google ELB
    
    Service ID: gelb
    
    Description: Service for Google Load Balancer
    
    Category: Load Balancer or custome service
    
# External Lifecycle Actions:
    External Action Bundle:  URL 
    
    URL : http://35.154.153.188/gelb/gelb.zip<location of gelb.zip> 
    
    Download the Google Load Balancer Service Bundle : http://35.154.153.188/gelb/gelb.zip
    To add the Google Load Balancer service login to CloudCenter as an administrator and click on Admin -> Services -> Add Service. The information below should be used to create the Google service.
    
    
    
    
    
# External Lifecycle Actions:
External Action Bundle: 
URL : http://35.154.153.188/gelb/gelb.zip<location of gelb.zip> 
Start:
Script from bundle: service start
Stop:
Script from bundle: service stop
# Deployement Parameters:
| Parameter Name	| Type	 | Description | Allowed Value |Default Value |
| ------ | ------ | ------ |------ | ------ |
| gelbProjectname | string | The project id where the service need to be deployed.| <samplename> |  |
| gelbLoadBalancerType |	List |	Type of Load Balancer. For more details on the type of load balancer to choose, check Google cloud documentation | TCP / HTTP / UDP | 
|gelbInstances | String | Comma separated instance names to be configured for the service. Ensure the configured health check path is  available and is responding in all the specified instances for the configured health check to pass
| gelbHealthCheck |	String |	The health check name to be configured for the service. | 

once the deployement parameters filled and save the service file.




## App Profile Modeling.

1. From App profile select --> MODEL --> N- Tier Execution --> Service --> Custom service --> <select load balancer and drag and drop to topology model>
2. From Web server -<Select webserver drag and drop>
3. Connect webserver from Google load balancer 

And save App profile with <AppName>

## Deployments

From Deployment page select --> New Deployment and Select the App profile 
Start to Deploy with required Deployement parameters.


The Packer Service bundle consists of the following files:



# Shell script:
 - service: Initiates the python script to start integration.

# Python script :
 - install_setup.py: The script will installs necessary python packages also invokes external life cycle action.
- google_load_balancer.py: This script will have all lifecycle actions and checking required parameter from the Environment. It involves the creation and deletion of google load balancer using Google Api python client SDK

 - google_management.py: Script that invokes the main method in google load balancer to 
 - common.py: This script contains common functionalities which is required for other script files.
 - util.py: utility file
 - error_utils.py: A script that handles error functionalities
 

 
 
