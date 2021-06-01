+++
title = "Start Your Engines ! "
chapter = false
weight = 5
+++

![image](/images/workshop_setup/ad_team_tech_lead.png)

{{% notice warning %}}
You must **have enough available VPCs, Elastic IPs, and NAT Gatewways in the region you are working in** to successfully **create an EKS Cluster** with a managed node group of 2 nodes.  You also need to have space for three S3 Buckets. If you **run into a problem** during the setup, it is **usually associated with insufficient resources or permissions in your AWS account**.  You can resolve resource constraints by <a href="https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html" target="_blank">**requesting a quota increase**</a> for your AWS account.
{{% /notice %}}

{{% notice warning %}}
In order to prevent charges to your AWS account, we recommend cleaning up the infrastructure that gets created with the setup utility. If you plan to keep things running so you can examine the workshop a bit more, please remember to do the cleanup when you are done. It is very easy to leave things running in an AWS account, forget about it, and then accrue charges.
{{% /notice %}}

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Just so you understand ahead of time, you can easily clean up all the resources that get created by the setup utility by using the commands below:

```
cd /home/ec2-user/environment

./teardownWorkshop.sh 
```

<br>

## Let's do this ! <span style="color: #4e3eb1;"><i class='fas fa-cog fa-spin'></i></span>

<br>

Now that you've got all the prerequisites out of the way, you can kick off the initial setup steps and go grab a cup of coffee <i class='fas fa-coffee'></i> while the setup utility runs.

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Ensure you are in your home directory by executing the command below:

```
cd /home/ec2-user/environment
```

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Download the setup script using the following command:

```
curl --silent -L https://raw.githubusercontent.com/Appdynamics/appd_aws_observability_lab/main/setupWorkshop.sh -o ./setupWorkshop.sh
```

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Use the following command to make the script executable:


```
chmod +x setupWorkshop.sh
```

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Use five (5) letters of your first, and or, your last name to create your unique workshop user name using the command below:

**EXAMPLE:**&nbsp; export appd_workshop_user=TOMSM

```
export appd_workshop_user=<YOUR USER NAME>
```

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Use the command below to execute the setup script:

```
./setupWorkshop.sh
```


{{% notice info %}}
<span><i class='fas fa-hourglass-half fa-lg'></i></span> The setup utility takes **approximately 7 minutes to complete**.  While you're waiting for the setup to finish you can **go to the AppDynamics Advantage section** where you can **find out why AD Financial selected AppDynamics** as their **preferred observability solution**. <span><i class='fas fa-hourglass-half fa-lg'></i></span>
{{% /notice %}}



<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the start of the setup script should look like this:


![image](/images/workshop_setup/setup-output-start.png)


<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the setup script when it ends, should look like this:

![image](/images/workshop_setup/setup-output-end.png)


## What the setup utility does

**01)** Installs Java JDK 1.8 <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**02)** Resizes the Disk on your C9 instance <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**03)** Installs kubectl <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**04)** Installs eksctl <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**05)** Installs docker-compose <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**06)** Installs the AppDynamics Database agent <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**07)** Creates an EC2 security group for external access to RDS Databases <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**08)** Creates RDS databases with the security group attached <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**09)** Creates three S3 buckets <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**10)** Creates two Application Performance Monitoring apps in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**11)** Creates two Browser Real User Monitoring apps in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**12)** Creates two AppDynamics Database collectors in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**13)** Creates an RBAC User in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**14)** Creates an RBAC Role in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**15)** Adds the RBAC User in the AppDynamics Controller to the appropriate RBAC Roles <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**16)** Deploys the Pre-Modernization application to your local C9 instance <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**17)** Creates the teardown file


Using a shell script - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

Using the AWS Java SDK - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

Using the AppDynamics REST API - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>


## Additional setup in following sections

There will be some additional setup steps in the following sections listed below.  There's no need to do them now.  Wait until you've reached those sections to perform the steps for each section.

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Modernize Section

 - Create the EKS Cluster
 - Deploy the Application to EKS
 - Deploy the Server Agent to EKS

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Operate Section

 - Deploy the Cluster Agent to EKS

## What the final architecture will look like

![image](/images/workshop_setup/arch_diagram.png)

<br>

## Next <i class='fas fa-cog fa-spin'></i>

**While you are waiting** for the setup utility to finish, **go to the AppDynamics Advantage section** where you can **find out why AD Financial selected AppDynamics** as their **preferred observability solution**.
