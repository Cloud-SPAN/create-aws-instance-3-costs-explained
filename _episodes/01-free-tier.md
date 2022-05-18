---
title: "The AWS Free Tier"
teaching: 20
exercises: 10
questions:
- What does the AWS Free Tier cover?
- How to know your service usage is within the Free-Tier limits?
- How much will you pay should you exceed the Free-Tier limits?
objectives:
- Know the scope and limits the AWS Free Tier.
- Know how to check your AWS service usage as compared to the Free-Tier limits?
- Understand how AWS billing works?
keypoints:
- The AWS Free Tier is available to any business or personal AWS account. 
- It has three schemes, *12 months free*, *Free Trials*, and *Always Free*, that apply to different types of service.
- Your instance uses *12 months free* services, EC2 compute and EBS storage services, and *Always Free* services, KMS login key management and Data Transfer services. 
- If you do not make changes to the configuration of the instance it will remain free
- If you increase the size of your instance or the number of instances and want the service to remain free, you will be need to make other adjustsments such as deleting instances before the end of the month.
- You can check your service usage as compared to the Free-Tier limits in the Billing Dashboard option **Free Tier** and your bills in the option **Bills**. Check the first one every few days.
---
> ## Prerequisites
> You will need to login to your AWS IAM user account to follow the second part of this episode; the instructions to login are in the lesson [Create and manage your AWS instance](https://cloud-span.github.io/create-aws-instance-2-manage-instance/01-create-aws-instance/).
{: .prereq}

# Introduction
The [AWS Free Tier](https://aws.amazon.com/free) covers more than 100 AWS services including the compute and storage services you used to create your instance in the previous lesson. Service usage covered by  the AWS Free Tier has limits, however, both in time and in capacity, and you will be billed as soon as you surpass these limits. 

The AWS Free Tier has three schemes (offers/plans): 
1. *12 months free*,
    Lasts for 12 months from the moment you opened your account and covers typical IT services such as servers, storage and networking. This scheme covers the instance you created in the last lesson but only if you created it using the t2.micro instance type we suggested; if so, you will not be billed for one year.

2. *Free Trials* 
    Covers more specialised services such as machine learning. It is valid either for short-term periods of 1-3 months of for a number of service invocations. Free Trials start from the date you start using a particular service and will terminate after the specified time period expires or the number of service invocations is reached. After that you will then be billed. 

3. *Always free*
   Covers a variety of services some of which have an auxiliary role. For example, you will recall that in using your instance you must use an encrypted key file to login to your instance and, through the program `ssh`, you enter shell commands and get data/results that are transferred between your local computer and your instance. In so doing, you are using two *always-free* services: the *AWS Key Management Service* to securely access your instance and the *AWS Data Transfer* service to tranfer data into and out from your instance. These services have always-free monthly quotas of 20,000 requests and 100 GB respectively. If you surpass those quotas in a month, you will be billed. 

In the remainder of this episode we will only cover the Free-Tier aspects that apply to the instance your created in the last lesson:

> ## Topics covered:
>
> 1. **Services used by your instance and their Free-Tier usage quotas**.\
> You will learn what services comprise your instance, their free usage limits, and how the usage limits are applied.
>
> 2. **Checking your service usage as compared to Free-Tier quotas**.\
> You will learn how to check your service usage and how service usage is measured and billed.
>
> 3. **Understanding your bills**.\
> You will learn how bills are organised and how billing is applied.
{: .callout}


# 1. Services used by your instance and their Free Tier usage quotas

The instance you created in the previous lesson uses these Free-Tier services:
- Amazon Elastic Compute Cloud (EC2) --- 12-months free with a monthly quota
- Amazon Elastic Block Storage (EBS)  --- 12-months free with a monthly quota
- AWS Key Management Service (KMS) --- always-free 20,000 requests per month
- AWS Data Transfer (DT) service --- always-free 100 GB per month

This section covers EC2 and EBS. KMS and DT are covered in the next section.

To find out about the EC2 and EBS services and their free quotas, go to the [AWS Free Tier](https://aws.amazon.com/free) web page and scroll down with the mouse until you see the heading **Free Tier Details** on the left below (no need to login to your account yet). 

### The compute service of your instance: EC2

Check the **12 Months Free** box under the Tier Type filter. These shows the EC2 Free Tier detail that apply to your instance. Hovering the mouse over the boxes reveals more detail for each category of use (Compute, Storage, Database etc). Under Compute, you can have (1) you have 750 hours **per month**, which amounts to 750/31 = 24.19 hours for each day in a month; (2) you can use those hours running **Linux**, **RHLS** (Red Hat Enterprise Linux), and **SLES** (Suse Linux Enterprise Server) with instances of type **t2.micro** or **t3.micro** whichever is available in the region you create the instance, and (3) you can have other 750 hours per month to run Windows with instances of type **t2.micro** or **t3.micro** whichever is available in the region you create the instance.

![Caption.](../fig/02-ec2-free-tier.png "EC2 compute Free Tier details for each category of use. The Compute category is highlighted so the full detials are shown.")


This means that you can run your t2.micro instance continuously until your Free Tier expires without incurring any cost, but see notes below. 

> ## Remember this:
> - The 750 hours for Linux instances cannot be combined with the 750 hours for Windows intances.  
> - The 750 hours for Linux and Windows instances apply globally to your account, not to a region and not to an instance. That is, the 750 hours in a month are divided among the number of Linux (or Windows) t2.micro instances that you run in the month in any region. You can run one instance continually for 750 hours or two for 375 hours or three for 250 hours etc.
> - Unused hours in a month do not roll over to the next month.
{: .callout}

### The storage service of your instance: EBS
Note that there are several different types of Storage.
To see the details of the EBS Free Tier that apply to your instance, scroll further down the AWS Free Tier web page until you see the Storage box labelled **Amazon Elastic Block Storage 30GB** and then hover the mouse cursor on the box.

For Amazon Elastic Block Storage 30GB Storage (1) you can use up to 30GB of EBS storage for 12 months; (2) the EBS storage can be **SSD** (Solid State Drive) storage or magnetic (previous generation) storage with up 2 million Input/Ouput (I/O) operations; and (3) you have up to 1GB of snapshot storage. 

![Caption.](../fig/03-ebs-free-tier.png "EC2 compute Free Tier details for each category of use. The Amazon Elastic Block Storage 30GB category is highlighted so the full detials are shown.")

The instance you created in the last lesson is using all 30 GB of SSD storage. 

Snapshots are used for backups but your instance does not perform any backups.

> ## Remember this:
> - The Free Tier 30 GBs EBS storage applies to your account. As your instance is using that many GBs, you cannot use more storage of any type (SSD or magnetic) without incurring some cost. Of those 30 GBs, 12 GBs are free for your data and applications.
{: .callout}

# 2. Checking your service usage is within Free Tier quotas

AWS bills users monthly and Free-Tier eligible services have monthly quotas or limits. You must not surpass these quotas in each month if you don't want to incur costs while your Free Tier is active. To find out how much in the current month you have used of your monthly Free-Tier allowance, login to your IAM account and go to the **Billing Dashboard** using the drop-down menu *user@accountalias* (or *user@accountnumber* if you did not create an alias) on the top right. Then, on the navigation pane on the left, under Billing, click on **Free Tier**. 
This shows you the Free Tier usage summary table.

![Caption.](../fig/05-free-tier-usage-excedeed01Table.png "Free Tier usage summary table.")

The table shows the usage in the current month of each Free-Tier eligible service in your account. There is a row for each service and the columns give: the type of **Service**, the **AWS Free Tier usage limit**, your **Current usage** for the month, the  **Forecasted usage** for the month, the  **MTD actual usage** for the month as a percentage of the service monthly Free-Tier limit, and the service **MTD Forecasted usage** for the month. **MTD** stands for Month-To-Date.

Any service created or used in a month will contribute to the corresponding service usage of the month even if the service is deleted early in the month.

The first two rows correspond to the **EBS storage** and the **EC2 compute** services presented earlier. Note that EBS storage ("30 GB of Amazon Elastic Block Storage") is of type *Amazon Elastic Compute Cloud*. This storage is part of your instance and will be deleted when your instance is deleted. You can detach the storage before deleting your instance if you want to preserve it. Note that there are other types of AWS storage such as S3 (Simple Storage Service) which you can use without attaching them to an instance. 

The third row corresponds to the login AWS **Key Management Service** which allows you to securely access your instance based on the login key pair you created when you created your instance. The Key Management service is an *always-free* service with up to **20,000 requests free** each month that apply globally to your account. That is plenty of requests. You don't really need to be concerned about it.

The fourth column corresponds to the AWS **Data Transfer** service which allows you to tranfer data into and out of your instance and any other services. It is *always-free* to transfer data out with up to **100 GB free** per month across all services you are using.  Data transfers **into** your instance/s (or other AWS services) are **free** --- but you may pay for storing the data; for example, if you transter data into your instance and your Free Tier has expired, you will be paying for EBS storage. 

### **Notes on service usage**

#### **Usage of EBS storage is measured in GB-Month**'s (GB-Mo in the table):
![Caption.](../fig/05-free-tier-usage-excedeed02EBS-row.png "EBS storage Free Tier usage table row.")

Under the free tier you have 30 GB-Months per month for 12 months. This means you can run one 30 GB instance for a month or one 60GB instance for half a month or two 30 GB instances for half a month. This is the case whether there are 28, 30 or 31 days per month so that the per day rate varies depending on the month.

> ## Example
> If you had two 30 GB instances running you can use them for
> -  30 / (2 x 30) * 28 days = 14 days in February
> -  30 / (2 x 30) * 30 days = 15 days in April
> -  30 / (2 x 30) * 31 days = 15.5 days in March
> 
> If you had a 50 GB instance running you can use it for
> -  30 / 50 * 28 days = 16.8 days in February
> -  30 / 50 * 30 days = 18 days in April
> -  30 / 50 * 31 days = 18.6 days in March
{: .callout}

Note that AWS uses actually seconds for calculations but we use hours here to simplify. See [EBS pricing](https://aws.amazon.com/ebs/pricing/).

> ## Important!
> If you decide to run more than one 30 GB instance (e.g., one 50 GB or two 30 GB) for a shorter time you must terminate your instance by the the time you reach the 30 GB-Month limit.
{: .prereq}

Let's see a billing example assuming your 12-month Free Tier has expired.

> ## After your 12-month Free Tier has expired
> In the Ireland region, the cost of EBS storage is US $ 0.11 per GB-Month (in April 2022).
>
> This means you pay $ 0.11 per GB per month.
> 
> If you create a 30 GB instance and delete it after 8 days you will pay:
> -  0.11 * 30 GB * 8/28 = $0.9428 in February
> -  0.11 * 30 GB * 8/30 = $0.88 in April
> -  0.11 * 30 GB * 8/31 = $0.8516 in March
{: .callout}


#### **Understanding "MTD actual usage" and "MTD forecasted usage"**

**MTD actual usage** is the total usage of a service in the current month, from the beginning of the month up to the last day before the current date. It is shown in the table as a percentage of the service Free-Tier quota to more easily appreciate how much of that quota has been used. It is computed thus for any service:

*service Current usage / service Free-Tier quota * 100*

![Caption.](../fig/05-free-tier-usage-excedeed03EBSnEC2rows.png "Free-Tier usage table showing the rows for EBS, EC2 and KMS. The column give the Freer-tier limit, the current usage, for forecasted use for the month, the MTD usage and the forecasted MTD usage for the month")

> ## Example MTD usage calculations:
> *service Current usage / service Free-Tier quota * 100*
> 
> The Free-Tier quota of Elastic Block Storage (EBS) is 30 GB per month. If your usage of EBS so far this month is 8 GB-Mo then you have used:
>           8 GB-Mo / 30 GB * 100  =  26.6%
>
> The Free-Tier quota of EC2 is 750 hours per month. If your usage of EC2 so far this month is 76 hours then you have used:
>          76 hours / 750 hours * 100 = 10.13%
>
> The Free-Tier quota of Key Management Service (KMS) is 20,000 requests per month. If your usage of KMS so far this month is 13 requests then you have used:
>           13 requests / 20,000 requests * 100 = 0.065%
>  
{: .callout}

Note that the Current Usage values are rounded for display but the exact values are used in calculation so you may see small differences between the table and your own calculations.

**MTD forecasted usage**  let's you know whether your current rate of use excceds that allowed under the free-tier.

> ## Remember this:
> If an **MTD forecasted usage** value in the AWS Free-Tier Summary table is higher than 100%, you should reduce your use of it. 
>
> If you have not changed the configuration of your instance, you should not exceed the free-tier limit and the instance will not incur a cost even if you don't stop or delete it. However, if you change its configuration by:
> - adding EBS storage or 
> - using an instance type with more capacity
> 
> Then you _could_ exceed the limit if you do not make adjustments.
> For example, if you double the EBS storage you will need to delete your instance half way through the month to stay within the limit. 
> Note: This course does not cover how to increase the EBS storage of your instance.
{: .callout}

# 3. Understanding your bills
You will be billed on the 3rd of 4th of each month but can access your bill any time in the Billing Dashboard. 
-  Login to your IAM account and go to the Billing Dashboard using the drop-down menu **user@accountalias** (or **user@accountnumber** if you did not create an alias) on the top right. 
-  Click **Bills** under Billing on the left

This will show a summary of the current month's bill. A drop-down menu, **Date** enables you access previous bills. 

![Caption.](../fig/06-aws-bill-page01.png "AWS Bills - Example 1.")

If you stay within the free-tier limit, the Service charges will remain at $0.
