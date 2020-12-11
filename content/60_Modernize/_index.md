+++
title = "Modernize"
chapter = false
weight = 60
+++


#### Alex is the Development Lead for the modernization project at AD Financial. &nbsp; He has been be working closely with Nathan to implement the modernized application, utilizing several AWS services. &nbsp; Alex understands how using modern cloud services, including container management technologies, can accelerate the performance, deployment, and management of mission critical applications.


![image](/images/modernize/ad_team_developer.png)

 

#### During the Modernization phase, Nathan and his team derived the following conclusions based on their findings:

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-sm'></i></span>&nbsp; The frontend web components were not the primary cause of high end user response times related to the loan approval process.

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-sm'></i></span>&nbsp; Business loan processing and personal loan processing need to be separated into multiple independent services so they can be independently scaled and maintained.

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-sm'></i></span>&nbsp; The need to have a more scalable, long-term archive storage solution for the loan audit data.  

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-sm'></i></span>&nbsp; The collocation of loan data and audit data was constraining the database and needed to be split into independent repositories.

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-sm'></i></span>&nbsp; The need to have monitoring intelligence down to the infrastructure layer for each component accessible within the same UI.

<br>

AWS offers multiple services for container orchestration and storage.  After careful consideration, the decision was made by the team to move forward with the following AWS stack that would best meet their technical and business requirements derived during the Mobilization phase.


&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-check-square'></i></span>&nbsp; **Container Orchestration Selection**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #efc100;"><i class='fas fa-certificate'></i></span>&nbsp; **AWS Elastic Kubernetes Service (EKS)**

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-check-square'></i></span>&nbsp; **Storage Solution Selection**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #efc100;"><i class='fas fa-certificate'></i></span>&nbsp; **AWS Simple Storage Service (S3)**

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-check-square'></i></span>&nbsp; **Database Solution Selection**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #efc100;"><i class='fas fa-certificate'></i></span>&nbsp; **AWS Relational Database Service (RDS)**



For container orchestration **EKS aligns well with the teams requirements**, having the ability **to automate scaling, managing, updating, and removing containers at will** without incurring any system downtime.

**S3 (Simple Storage Solution)** was chosen to host the audit data as it **provides an affordable and robust solution** to securely archive the needed audit trail while supporting high retrieval and ingestion rates with the ability to scale dynamically.

**AWS RDS was chosen** as the new database backend as it **provides the high availability and fault tolerance needed** with **real time replication across multiple availability zones and/or regions**.

![image](/images/modernize/app_arch_diag.png)


{{% notice info %}}
**Optional:**  You can explore the artifacts that were utilized to deploy the application and AppDynamics agents associated with this section by navigating to the following directories listed below that are located on your Cloud9 instance: 
{{% /notice %}}

```
/home/ec2-user/environment/deployment

/home/ec2-user/environment/deployment/post-mod-kube-cluster

/home/ec2-user/environment/deployment/post-mod-kube-app

/home/ec2-user/environment/deployment/post-mod-kube-ma
```

## Next <i class='fas fa-cog fa-spin'></i>

Let’s follow Alex and his team as they **utilize AppDynamics, having purpose built integrations for AWS** that **provides application performance monitoring continuity** throughout the **entire application modernization architecture lifecycle**. 
