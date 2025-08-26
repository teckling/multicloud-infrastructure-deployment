# multicloud-infrastructure-deployment
A bash scripting automation tool that can deploy multiple web applications to any one of AWS, Azure or Google clouds.

This project primarily aim to create a structure of file system and folders whereby automation scripts written primarily in aws cli, az cli, or gcloud cli by RnD engineers can be grouped together under one "roof". The automation scripts thus created can be used by end user to deploy different web applications to either AWS, Azure or Google cloud. The end user of this automation script only need to remember simple commands. For example:

deploy for_company_A app01 azure

deploy for_customer_B app02 gcloud

When the above commands get run, the automation script will start deploying VPC and subnets, VM, loadbalancer, storage bucket, security group, database etc, and pull down software from either github, s3, bitbucket or other sources and deploy it to the specific cloud.

The end user is not required to know aws cli, azure cli, or gcloud cli in great details when doing the deployment. Although such knowledge is beneficial if automation script failed requiring troubleshooting e.g. create VM failed because quote limit is reached.

In addition to the aforementioned cloud cli, this project will also aim to show that various management configuration tools such as ansible, salt, puppet can also be group together under this same "roof", and being used in the deployment of web application.

In short, we are going to group aws/azure/gcloud CLI scripts and ansible, salt, puppet all under one big folder.

With this structure, each RnD engineer can choose his or her preferred cli and tools. The script that he creates can be used by other RnD engineers as well, either by expanding or modifying existing content, or copy and modify in separate sub-folders.

(i) For example, Engineer_A may be more familiar with gcloud CLI and salt, he thus choose these to write his deployment script for app01. In some subfolder under this one big folder.

(ii) Engineer_B may be more familiar with Azure CLI and ansible, and thus he choose these to write his deployment scripts for app02. Also in some subfolder under this one big folder.

(iii) Engineer_C, seeing that there are already script for gcloud and azure, thus decide to contribute by writing automation script in AWS CLI, but decide salt is also his preferred management config tool, thus copy that whole salt folder created by Engineer_A and made modification before using. Also in some subfolder under this one big folder.

(iv) if a customer request to have his application deploy in Alibaba cloud, automation script can be developed inside this one big roof as well.

The end user might receive request to deploy app01 for company XYZ to aws . All he need to do is e.g. deploy XYZ app01 aws. If at a later date XYZ decided to deploy app01 to Azure, then all the engineer need to do is to issue the following commands:

decommission for_company_A app01 aws

deploy for_company_A app01 azure

Notice that end user only need a rudimentary knowledge of different clouds available. End user does not even need to know which managment configuration tool is being use behind the scene, as these are mostly decided by the RnD engineers who write the automation scripts. However, knowledge of CLI and management configuration tool can still be useful if something failed to work, and cryptic error message appear on the screen, requiring further troubleshooting. This happen all the time.

It is expected that all engineers who write automation scripts that contribute to this structure take the following into consideration:

(1) always include at least one monitoring tool in your deployment e.g. zabbix, grafana, or prometeus so that end user can use this monitoring tool to monitor every component in the application environment that they deployed

(2) Daily/weekly/monthly cost/billing information should be made available. May be using the monitoring tool mentioned in (1) above. We want to be able to see cost per cloud, per region, per customer etc.

(3) preferrably, there should be an alert system, so that if a fault occurred e.g. lost connection to mysql database, a phone call can be made to an on-duty engineer who can investigate and rectify the fault.

(4) the application enviroment thus created by the script should meet popular industry security and operation standards e.g SOC2, ISO 27001. Preferrably, the automation script may regularly collect informations on the application environment that can be used in internal or external audits involving security and operation.

(5) Keep in mind disaster recovery requirement. If a certain application is down due to cloud provider problem in North Virginia, we can quickly deploy the same environment to Sydney Australia, within reasonable downtime.

(6) Keep in mind granular recovery requirement. Sometime it just does not make sense to rollback 3 hours or 6 hours earlier to recover some old data for customer A, but you lost 3 or 6 hours of new data for customer B. We want to recover old data for customer A without losing new data for customer B.

Have fun.
