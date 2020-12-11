+++
title = "Start Your Engines ! "
chapter = false
weight = 5
+++

![image](/images/workshop_setup/ad_team_tech_lead.png)

{{% notice warning %}}
You must **have enough available VPCs, Elastic IPs, and NAT Gatweways in the region you are working in** to successfully **create an EKS Cluster** with a managed node group of 2 nodes.  You also need to have space for three S3 Buckets. If you **run into a problem** during the setup, it is **usually associated with insufficient resources or permissions in your AWS account**.  You can resolve resource constraints by <a href="https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html" target="_blank">**requesting a quota increase**</a> for your AWS account.
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

Now that you've got all the prerequisites out of the way, you can kick off the final setup steps and go grab a cup of coffee <i class='fas fa-coffee'></i> while the setup utility does the rest.

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

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Use the command below to execute the setup script::

```
./setupWorkshop.sh
```


{{% notice info %}}
<span><i class='fas fa-hourglass-half fa-lg'></i></span> The setup utility takes **approximately 28 minutes to complete**.  While you're waiting for the setup to finish you can **go to the AppDynamics Advantage section** where you can **find out why AD Financial selected AppDynamics** as their **preferred observability solution**. <span><i class='fas fa-hourglass-half fa-lg'></i></span>
{{% /notice %}}



<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the setup script when the EKS cluster is created, should look like this:

<span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-sm'></i></span> EKS cluster creation as part of the complete setup, takes approximately 15 minutes of the total time.

![image](/images/workshop_setup/setup-output-eks.png)


<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the setup script when it ends, should look like this:

![image](/images/workshop_setup/setup-output-end.png)


## What the setup utility does

![image](/images/workshop_setup/arch_diagram.png)


**01)** Installs Java JDK 1.8 <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**02)** Resizes the Disk on your C9 instance <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**03)** Installs kubectl <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**04)** Installs eksctl <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**05)** Installs docker-compose <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**06)** Installs the AppDynamics Database agent <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**07)** Creates an EC2 security group for extenal access to RDS Databases <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**08)** Creates RDS databases with the security group attached <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**09)** Creates three S3 buckets <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**10)** Creates two Application Performance Monitoring apps in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**11)** Creates two Browser Real User Monitoring apps in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**12)** Creates two AppDynamics Database collectors in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**13)** Creates an RBAC User in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**14)** Creates an RBAC Role in the AppDynamics Controller <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**15)** Adds the RBAC User in the AppDynamics Controller to the appropriate RBAC Roles <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**16)** Creates the EKS Cluster <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**17)** Deploys the Post-Modernization application to the EKS Cluster <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**18)** Waits for the application to initialize in the EKS Cluster

**19)** Deploys the AppDynamics Machine agent to the EKS Cluster <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**20)** Deploys the AppDynamics Cluster agent to EKS Cluster <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**21)** Exposes the website front end with an ELB in the EKS Cluster <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**22)** Deploys the Pre-Modernization application to your local C9 instance <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

**23)** Creates the teardwown file


Using a shell script - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

Using the AWS Java SDK - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

Using the AppDynamics REST API - <span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span><span style="color: #4e3eb1;"><i class='fas fa-asterisk fa-xs'></i></span>

<br>

## Next <i class='fas fa-cog fa-spin'></i>

**While you are waiting** for the setup utility to finish, **go to the AppDynamics Advantage section** where you can **find out why AD Financial selected AppDynamics** as their **preferred observability solution**.
