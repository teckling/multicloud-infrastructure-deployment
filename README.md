# multicloud-infrastructure-deployment
A bash scripting automation tool that can deploy multiple web applications to AWS, Azure or Google clouds.

This project primarily aim to create a structure of file system and folders whereby automation scripts written primarily in aws cli, az cli, or gcloud cli can be grouped together in one big folder. The automation scripts thus created can be used by end user to deploy different web application to either AWS, Azure or Google cloud. The end user of this automation script only need to remember simple commands. For example:

deploy app01 azure

deploy app02 gcloud

The end user is not required to know aws cli, azure cli, or gcloud cli in great details.

In addition to the aforementioned cloud cli, this project will also aim to show that various management configuration tools such as ansible, salt, puppet can also be group together in this folder structure and use in the deployment of web application.

With this structure or arrangement, RnD engineers can choose their preferred cli and tools.

(i) For example, Engineer_A may be more familiar with gcloud CLI and salt, he thus choose these to write his deployment script for app01.

(ii) Engineer_B may be more familiar with Azure CLI and ansible, and thus he choose these to write his deployment scripts for app02. 

(iii) Engineer_C, seeing that there are already script for gcloud and azure, thus decide to contribute by writing automation script in AWS CLI, but decide salt is also his preferred management config tool, thus copy that whole salt folder created by Engineer_A and made modification before using.

The end user might receive request to deploy app01 for company XYZ to aws . All he need to do is e.g. deploy XYZ app01 aws. If at a later date XYZ decided to deploy app01 to Azure, then all the engineer need to do is to issue:

destroy XYZ app01 aws

deploy XYZ app01 azure

Notice that end user only need a rudimentary knowledge of different clouds. End user does not even need to know which managment configuration tool is being use behind the scene, as these are mostly decided by the engineer who writes the automation scripts. However, knowledge of CLI and management configuration tool can still be useful if something failed to work, and cryptic error message appear on the screen, requiring further troubleshooting.

It is expected that all engineers who write automation scripts that contribute to this structure take the following into consideration:

(1) always include at least one monitoring tool into your deployment e.g. zabbix, grafana, or kubernetes so that end user can use this monitoring tool to monitor every component in the app environment that they deployed

(2) preferrably, there should be an alert system, so that if a fault occurred e.g. lost connection to mysql database, a phone call can be made to an on-duty engineer who can investigate and rectify the fault

(3) the app enviroment thus created by the script should meet popular industry security and operation standards e.g SOC2, ISO 27001. Preferrably, the automation script may regularly collect informations on the app environment that can be used in internal or externa audits.
