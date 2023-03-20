+++
title = "Deployment"
chapter = false
weight = 1
+++

![image](/images/modernize/ad_team_developer.png)

In this section you'll be performing the following setup and deployment steps:
 - Create a two node EKS cluster
 - Deploy the application to EKS
 - Deploy the server agent to EKS


## Create the EKS Cluster

Let's start by looking at the script that creates the EKS cluster using the commands below in your Cloud9 terminal:

```
cd /home/ec2-user/environment/modernization_workshop

cat -n create_eks_cluster.sh
```

The script calls <a href="https://eksctl.io" target="_blank">**eksctl**</a> passing the **cluster.yaml** file to provide the cluster definition.

Take a quick look at the **cluster.yaml** file using the commands below:

```
cd /home/ec2-user/environment/modernization_workshop/applications/post-modernization

cat -n cluster.yaml
```
Notice where we've defined the name of the cluster, the region and availability zones to deploy to, the instance type for the nodes. and the number of nodes. 


{{% notice info %}}
Notice that the **default availability zones defined** in the **cluster.yaml file** are **a** and **c** on line number 9 in the image below.  It is advisable to run the command below to check that both of those availability zones are supported in your region.  You can **use the command below** to check the **supported availability zones in your region**. You can read more information about checking availability zones <a href="https://aws.amazon.com/premiumsupport/knowledge-center/vpc-find-availability-zone-options/" target="_blank">**here**</a>.  You **may need to edit** the **cluster.yaml** file to change the availability zones to the ones supported in your region before your create the EKS cluster.
{{% /notice %}}


Example command to check for supported availability zones if your region is **us-east-2**
```
aws ec2 describe-availability-zones --region us-east-2
```



![image](/images/modernize/kube-conf-01.png)

{{% notice warning %}}
You must **have enough available VPCs, Elastic IPs, and NAT Gateways in the region you are working in** to successfully **create an EKS Cluster** with a managed node group of 2 nodes.  If you **run into a problem** during the setup, it is **usually associated with insufficient resources or permissions in your AWS account**.  You can resolve resource constraints by <a href="https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html" target="_blank">**requesting a quota increase**</a> for your AWS account.
{{% /notice %}}

Go ahead and create the EKS cluster using the commands below:
 - cluster creation takes ~16 minutes to finish so please be patient and let the process complete

```
cd /home/ec2-user/environment/modernization_workshop

./create_eks_cluster.sh
```

The image below shows what the output looks like for the EKS cluster creation. 

![image](/images/modernize/kube-deploy-01.png)

<br>

## Deploy the Application to EKS

Now that the EKS cluster is up and running, use the commands below to deploy the modernized application to EKS:
 - deployment and initialization takes ~3 minutes to finish

```
cd /home/ec2-user/environment/modernization_workshop

./deploy_eks_application.sh
```
<!--
{{% notice warning %}}
If the **deploy_eks_application.sh** hangs or gets stuck, you can CTRL+C (Windows) or CMD+C (Mac) to exit the script and re-run it.
{{% /notice %}}
-->

The image below shows what the output looks like for the application deployment and initialization.

![image](/images/modernize/kube-deploy-02.png)

<br>

## Deploy AppDynamics Agents

Use the commands below to **deploy the AppDynamics agents** to the EKS Kubernetes cluster.

```bash
cd /home/ec2-user/environment/modernization_workshop

./deploy_appdynamics_agents.sh
```

The output should look like the image below.

![image](/images/modernize/kube-conf-02.png)


### What AppDynamics agents were deployed and how?

Though there are several different ways to deploy these agents, we've used the <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/monitor-kubernetes-with-the-cluster-agent/install-the-cluster-agent/install-the-cluster-agent-with-helm-charts" target="_blank">**AppDynamics Helm Chart**</a> that simplified the deployment of agents to the Kubernetes clusters.

Below is the list of agents deployed by the Helm chart:

- <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/monitor-kubernetes-with-the-cluster-agent/overview-of-cluster-monitoring" target="_blank">**Cluster Agent**</a>
- <a href="https://docs.appdynamics.com/latest/en/application-monitoring/install-app-server-agents/java-agent" target="_blank">**Java APM Agent**</a>
- <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/server-visibility" target="_blank">**Server Visibility Agent**</a>
- <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/network-visibility" target="_blank">**Network Visibility Agent**</a>
- <a href="https://docs.appdynamics.com/latest/en/application-security-monitoring" target="_blank">**Secure Application Agent**</a>


### How is the Helm chart configured?

In our deployment we are overriding the <a href="https://github.com/CiscoDevNet/appdynamics-charts/blob/master/cluster-agent/values.yaml" target="_blank">**helm chart default *values.yaml* file**</a> to provide the specific configuration for our environment.

Use the command below in your Cloud9 terminal to view the template file used to generate the final version of the values.yaml file that is used in our deployment.

```bash
cat -n /home/ec2-user/environment/modernization_workshop/applications/post-modernization/clusteragent/values-ca1.yaml
```

- On **line 1 and line 2** we are specifying that we want to **deploy the Cluster Agent and the Server Visibility Agent**.
- On **lines 6 through 11** we- On **lines 6 through 11** we will provide the <a href="https://docs.appdynamics.com/latest/en/application-monitoring/install-app-server-agents/agent-to-controller-connections" target="_blank">**connection details**</a> to the **AppDynamics Controller**.
- On **lines 8 and 9** the username and password for **an AppDynamics Controller user with elevated privilages** are required only if you are configuring **Auto-Instrumentation of APM Agents** which we'll look at in the next section. 

![image](/images/modernize/kube-conf-03.png)

- On **line 15** we are **specifying the namespace(s)** we want the **Cluster Agent to monitor**.
- On **lines 17 through 33** we see the <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/monitor-kubernetes-with-the-cluster-agent/auto-instrument-applications-with-the-cluster-agent" target="_blank">**configuration**</a> for the <a href="https://docs.appdynamics.com/latest/en/infrastructure-visibility/monitor-kubernetes-with-the-cluster-agent/auto-instrument-applications-with-the-cluster-agent" target="_blank">**Auto-Instrumentation of APM Agents**</a>
- In this case we have **one instrumentation rule** defined for the **Java APM Agent** to label match on deployments with the **framework: java** label, as seen on **lines 28 and 29**
- Also, take note of **lines 21 through 24** where we are telling the auto-instrumentation to use the Application Name we have defined here and to use the Tier Names that are set for each service deployment in their **Kubernetes deployment Yaml file** which we will look at an example of next

![image](/images/modernize/kube-conf-04.png)


Now let's take a look at the Kubernetes deployment Yaml file for the **AccountManagement** service deployment to see how we used the label match from the **Auto-Instrumentation section** of the **values-ca1.yaml** used to deploy the AppDynamics agents, using the command below.

```bash
cat -n /home/ec2-user/environment/modernization_workshop/applications/post-modernization/application/account-management.yaml
```

- On **line 6** we are providing the label that matches to **line 29 in the values-ca1.yaml file** that tells the Cluster Agent to auto-instrument this deployment.
- On **line 7** we are providing the label that matches to **line 24 in the values-ca1.yaml file** that tells the Java Agent to use the Tier Name of **AccountManagenment** for this deployment.
- On **lines 24 through 26** we are referencing the **modernization_workshop/applications/post-modernization/application/config-map.yaml** for some of the required environment variables for the application
- On **lines 27 through 41** we are setting some required environment variables for this specific deployment/service in an in-line fashion

![image](/images/modernize/kube-conf-05.png)



<!--
Let's take a look at how the application and the Java APM agent were configured for EKS deployment.  We've used the **config-map.yaml** file to define the properties needed by the agent to connect to the controller.  The setup script you executed in the workshop setup section, auto-populated the agent to controller configuration properties for you just like the **application.env** file used for the Docker Compose application.  You can read more about the Agent to Controller Connection properties <a href="https://docs.appdynamics.com/appd/23.x/latest/en/application-monitoring/install-app-server-agents/agent-to-controller-connections" target="_blank">**here**</a>

Take a look at the **config-map.yaml** file using the commands below:

```
cd /opt/appdynamics/workshopuser/post-mod-kube-app

cat -n config-map.yaml
```

Notice that we've defined the Tier and Node names here in one place instead of each service deployment file.  Next we'll take a look at how we reference those within the **account-management.yaml** file used to deploy the AccountManagement service along with the way we configured the Java APM agent. 

![image](/images/modernize/kube-conf-02.png)


Use the commands below to examine the **account-management.yaml** file:

```
cd /opt/appdynamics/workshopuser/post-mod-kube-app

cat -n account-management.yaml
```

In the section of the file seen below, we are defining the Java Agent in an **initContainer** and referencing a pre-built Docker image of the Java Agent.

**Where do we** reference the Docker image of the Java Agent **?**
 - on **line 18** we are providing the reference to the pre-built public image that can be found <a href="https://hub.docker.com/r/appdynamics/java-agent/tags?page=1&ordering=last_updated" target="_blank">**here**</a>

**How do we** expose the directory on the image where the Java Agent binaries can be accessed by the application container that references it **?**
 - on **lines 21 - 22** we are specifying the details for the volume mount

![image](/images/modernize/kube-conf-03.png)


Starting on **line 26** we see the first part of the **definition for the *"account-management"*** application container.

**Notice** that the account-management container has its own image defined containing just the application code (e.g. **line 28**).

**How does the** Java Agent obtain its connection properties to the controller **?**
 - on **line 29 - 31**, we're pulling in the reference to the "config-map.yaml" file that contains those as well as the APM application name

**How does the** Java Agent get bootstrapped into the application JVM startup **?**
 - on **line 36**, we're telling Kubernetes to add the Java Agent bootstrap parameter to the JVM startup

![image](/images/modernize/kube-conf-04.png)

**How does the** *account-management* container get its Tier and Node name assigned **?**
 - on **line 45 - 49**, we are assigning the **Tier name** by pulling in a specific variable from the "config-map.yaml"
 - on **line 54 - 58**, we are assigning the **Node name** by pulling in a specific variable from the "config-map.yaml"
 - on **line 51 - 52**, we are telling the Java Agent to reuse the Node names when containers are recycled

**How do we** load the binaries for the Java Agent into the application container **?**
 - on **line 64 - 66**, we are pulling in the shared volume/directory from the Java Agent Init Container

![image](/images/modernize/kube-conf-05.png)


You can read more about using the Java Agent with Init Containers <a href="https://docs.appdynamics.com/appd/23.x/latest/en/application-monitoring/install-app-server-agents/java-agent/install-the-java-agent/install-the-java-agent-in-containers#id-.InstalltheJavaAgentinContainersv23.1-init" target="_blank">**here**</a>


You can read more about building the Java Agent into your own Docker Image <a href="https://docs.appdynamics.com/appd/23.x/latest/en/application-monitoring/install-app-server-agents/java-agent/install-the-java-agent/install-the-java-agent-in-containers#id-.InstalltheJavaAgentinContainersv23.1-dockerfile" target="_blank">**here**</a>

<br>

## Deploy the Server Agent to EKS

The final deployment step in this section will be deploying the Server Agent to the EKS cluster using the commands below:

```
cd /opt/appdynamics/workshopuser

./deployMachineAgent.sh
```

The image below shows what the output looks like for the Server Agent deployment.

If you see any warnings or an error in the output, just ignore them.

![image](/images/modernize/kube-deploy-03.png)

The Server Visibility Agent when deployed to Kubernetes **differs** from the Java Agent in that:

- the Server Visibility Agent should be deployed as a DaemonSet
- it runs in its own container within its own JVM on each node in the cluster
- the Server Visibility Agent does not require the definition of an application, tier, or node name, since it scans the process list/containers on the node to find AppDynamics APM agents in use and relates itself to those processes/containers

The Server Visibility Agent when deployed to Kubernetes **is similar to** the Java Agent in that:
- it will use the same controller connection properties defined in the *config-map.yaml* file 
- we are using a pre-built Docker image of the agent for this workshop
- you have the option of building your own Docker image of the agent in your own repository

Use the commands below to view the **machine-agent.yaml** file used to deploy the agent:

```
cd /opt/appdynamics/workshopuser/post-mod-kube-ma

cat -n machine-agent.yaml
```
Scroll down the file until you get to **line 16**.  Here we see the container **definition for the *"appd-infra-agent"*** AKA the Server Visibility Agent.

We are defining the Server Visibility Agent container and referencing a pre-built Docker image for it on **line 17** that can be found <a href="https://hub.docker.com/r/appdynamics/machine-agent-analytics/tags?page=1&ordering=last_updated" target="_blank">**here**</a>

**How does the** Server Visibility Agent obtain its connection properties to the controller **?**
 - on **line 26 - 28**, we're pulling in the "config-map.yaml" file that contains those properties

**What additional** properties are needed for the agent **?**
- the property on **line 20** is required if you want to collect more than minimal host level metrics
- it is highly recommended to replicate **lines 22 - 24** as well if using an older agent version

![image](/images/modernize/kube-conf-06.png)

You can read more about building the Server Visibility Agent into your own Docker Container Image <a href="https://github.com/Appdynamics/appdynamics-docker-images/tree/master/appd-machine-agent-analytics" target="_blank">**here**</a>

-->

<br>

## Database Visibility Agent

The AppDynamics Database Agent is a standalone Java program that collects performance metrics about your database instances and database servers. You can deploy the Database Agent on any machine running Java 1.8 or higher. The machine must have network access to the AppDynamics Controller and the database instance that you want to be monitored.

A single database agent can monitor multiple databases at once by using multiple database collector configurations.  The workshop setup utility installed the agent on your Cloud9 instance and also created two database collector configurations inside the controller.  You can see the running agent process by using the command below:

```
ps -ef | grep db-agent
```

In the case of the database agent, JVM command line properties were used to connect the agent to the controller.  Take notice of the "-Ddbagent.name" property.  This property is used to link a specific database agent to a database collector configuration.  Most of these properties could have optionally been defined in the agents configuration file, which can be seen by using the commands below:

```
cd /opt/appdynamics/dbagent/conf

cat controller-info.xml
```

The image below shows an example of the database collector configuration to monitor the MySQL database used in the post-modernized EKS application.  

Once the database agent is running with a specific name, its name should appear in the drop-down of available agents so you can associate it with the collector you're creating.  Since this is an RDS database, we have used the RDS endpoint as the hostname.  We can use the port "3306" for the DB since we have exposed it specifically in the VPC Security Group for the database.

You can see that we have used the "root" username and password to connect to the database and monitor it.  The recommended practice is to create a specific database user in the database and apply specific permissions to it for monitoring purposes.

You can read more about deploying the database agent and configuring collectors <a href="https://docs.appdynamics.com/appd/23.x/latest/en/database-visibility/administer-the-database-agent" target="_blank">**here**</a> and <a href="https://docs.appdynamics.com/appd/23.x/latest/en/database-visibility/add-database-collectors" target="_blank">**here**</a>

![image](/images/modernize/kube-conf-07.png)


<br>

## Next <i class='fas fa-cog fa-spin'></i>

Let’s follow Alex and his team as they **utilize AppDynamics, having purpose built integrations for AWS** that **provides application performance monitoring continuity** throughout the **entire application modernization architecture lifecycle**.



<!---
{{% notice warning %}}
The Cloud9 workspace should be built by an IAM user with Administrator privileges,
not the root account user. Please ensure you are logged in as an IAM user, not the root
account user.
{{% /notice %}}
-->

<!---
{{% notice info %}}
This workshop was designed to run in the **Oregon (us-west-2)** region. **Please don't
run in any other region.** Future versions of this workshop will expand region availability,
and this message will be removed.
{{% /notice %}}
-->

<!---
{{% notice tip %}}
Ad blockers, javascript disablers, and tracking blockers should be disabled for
the cloud9 domain, or connecting to the workspace might be impacted.
Cloud9 requires third-party-cookies. You can whitelist the [specific domains]( https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading).
{{% /notice %}}
-->



