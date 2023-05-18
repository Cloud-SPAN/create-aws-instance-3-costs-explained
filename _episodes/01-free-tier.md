---
title: "The AWS Free Tier"
teaching: 20
exercises: 10
questions:
- How much will your instance cost?
- What covers the AWS Free Tier?
- How to know your service usage is within the Free-Tier limits?
- How much will you pay should you exceed the Free-Tier limits?
objectives:
- Know the scope and limits of the AWS Free Tier.
- Know how to check your AWS service usage as compared to the Free-Tier limits?
- Understand how AWS billing works?
keypoints:
- The AWS Free Tier is available to any business or personal AWS account. 
- It has three schemes, *12 months free*, *Free Trials*, and *Always Free* that apply to different types of service.
- Your instance may use *12 months free* services, EC2 compute and EBS storage services, and *Always Free* services, KMS login key management and Data Transfer services. EC2 and EBS free service quotas **only apply** to instances using t2.micro instance type and up to 30 GB storage.
- You can easily check your service usage as compared to the Free-Tier limits in the Billing Dashboard option **Free Tier** and your bills in the option **Bills**. Check the first one every few days.
---
> ## Prerequisites
> You will need to login to your AWS IAM user account to follow the second part of this episode; the instructions to login are in the lesson [Create and manage your AWS instance](https://cloud-span.github.io/create-aws-instance-2-manage-instance/01-create-aws-instance/).
{: .prereq}

# Introduction
The [AWS Free Tier](https://aws.amazon.com/free) covers more than 100 AWS services including the compute and storage services you used to create your instance in the previous lesson. Service usage covered by  the AWS Free Tier has limits, however, both in time and in capacity, and you will be billed as soon as you surpass these limits.  The AWS Free Tier has three schemes (plans /offers): 
1. *12 months free*
2. *Free Trials*
3. *Always free*

The *12 months free* scheme lasts for 12 months from the moment you opened your account and covers typical IT services such as servers, storage and networking. This scheme will cover the instance you created in the last lesson **but only** if you created it by combining the Genomics AMI with the instance type t2.micro; if so, you will not be billed for one year.

The *Free Trials* scheme covers somewhat more specialised services such as machine learning. It is valid either for short-term periods of 1-3 months or for a number of service invocations. Free Trials start from the date you activate (start using) a particular service and will terminate after the specified time period expires or the number of service invocations is reached; you will then be billed for any usage of the service. 

The *Always Free* scheme covers a variety of services some of which have an auxiliary role. For example, you will recall that in using your instance you must use an encrypted key file to login to your instance and, through the program `ssh`, you enter shell commands and get data/results that are transferred between your local computer and your instance. In so doing, you are using two *always-free* services: the *AWS Key Management Service* to securely access your instance and the *AWS Data Transfer* service to tranfer data into and out from your instance. These services have always-free monthly quotas of 20,000 requests and 100 GB respectively. If you surpass those quotas in a month, you will be billed. 

> ## Topics covered:
>
> 1. [**The cost of your instance (no Free Tier)**](#1-the-cost-of-your-instance-no-free-tier).\
> You will learn what AWS services are used by your instance and the cost of your instance once the Free-tier period is finished.
>
> 2. [**Free-tier quotas related to your instance**](#2-free-tier-quotas-related-to-your-instance).\
> You will learn the Free-tier quotas related to your instance and whether they are applicable to your instance which depends on the configuration of your instance.
>
> 3. [**Check your service use as compared to Free-tier quotas**](#3-check-your-service-use-as-compared-to-free-tier-quotas).\
> You will learn how to check your service usage and how service usage is measured and billed.
>
> 4. [**Understanding your bills**](#4-understanding-your-bills).\
> You will learn how bills are organised and how billing is applied.
{: .callout}

# 1. The cost of your instance (no Free Tier)
The instance you created in the previous lesson makes use of these services:
- Amazon Elastic Compute Cloud (EC2) 
- Amazon Elastic Block Storage (EBS) 
- AWS Key Management Service (KMS) 
- AWS Data Transfer (DT) service 

The cost of your instance depends on the cost of those services and how much use your instance makes of each service. You may not incur any cost if the Free Tier is applicable but we will explore this scenario in the next section. 

In this section we are going to find out the cost your instance will incur when the Free Tier one-year period has finished, based on the use that your instance makes of those services. In so doing, we will present some data regarding those costs which were gathered from Amazon Web Service pages in May 2023. Note that the costs presented are those for AWS Region of Ireland.

### Compute (EC2) cost
The compute cost of your instance is determined by the **instance type** you chose in creating your instance. The table below shows the cost per hour, number of processors (vCPUs), and main memory size of the instance types so far mentioned in the course (there many more instance types). The data in the table was taken from the [Amazon EC2 On-demand Pricing](https://aws.amazon.com/ec2/pricing/on-demand/) page.

> ## The cost and specifications of AWS instance types relevant to this course
>
> | Instance type | On-demand hourly rate | vCPUs | Main memory | Comments
> |---------------|-------------|---------------|----|----|----|----|
> | t2.micro |	$0.0126 | 1 | 1 GiB | Free tier eligible --- suggested for your Genomics instance |
> | t3.micro |	$0.0114	| 2 | 1 GiB | Free tier eligible --- only if t2.micro is not available in the AWS region where the instance is created |
> | t3.small |	$0.0228	| 2 | 2 GiB	| Used for Cloud-SPAN Genomics workshop instances |
> | t3.2xlarge | $0.3648 |	8 |	32 GiB | Used for Cloud-SPAN Metagenomics workshop instances |	
{: .callout}

Based on the cost per hour in the table, the compute cost per day and per month in US dollars of the instance you may have created in the previous lesson will be:

| AMI - instance type | Compute Cost per day | Compute Cost per month |
|---------------|-------------|---------------|
| **Genomics - t2.micro** instance | $**0.3024** = $0.0126 x 24 hours | $**9.072** = $0.0126 x 24 hours x 30 days |
| **Genomics - t3.small** instance | $**0.5472** = $0.0228 x 24 hours | $**16.416** = $0.0228 x 24 hours x 30 days |
| **Metagenomics - t3.2xlarge** instance | $**8.7552** = $0.3648 x 24 hours | $**262.656** = $0.3648 x 24 hours x 30 days | 

> ## Your instance incurs **compute cost** only when it is running.
> Compute cost is billed per second, with a minimum of 60 seconds, see the [Amazon EC2 pricing](https://aws.amazon.com/ec2/pricing/) page and scroll down to the heading "Per-second billing". Thus even though AWS presents the cost per hour, you will be charged for the minutes your instance is running. 
{: .callout}

### Storage (EBS) cost
The storage cost of your instance is determined by the **size** of the **Cloud-SPAN AMI** you chose in creating your instance. The size of the Genomics AMI is 30 GB, while the size of both Metagenomics AMIs is 240 GB.

There are different types of EBS storage, each type with a different price, as described in the [Amazon EBS pricing](https://aws.amazon.com/ebs/pricing/) page. 

The type of storage used by all Cloud-SPAN AMIs is *General Purpose SSD (gp2) Volumes* and its cost is US $**0.11** per GB-month of provisioned storage. That is:

*Storage cost* &nbsp; = &nbsp; 0.11 &nbsp; x &nbsp; provisioned_storage_size &nbsp; x &nbsp; time_units_used &nbsp; / &nbsp; total_time_units_in_month

Thus the storage cost per day and per month in US dollars of the instance you may have created in the previous lesson will be:

| AMI - storage size | Storage Cost per day | Storage Cost per month |
|---------------|-------------|---------------|
| **Genomics - 30 GB** storage  | $**0.11** = $0.11 x 30 GB x 24 hours /(24 hours x 30-day month)| $**3.30** = $0.11 x 30 days |
| **Metagenomics - 240 GB** storage | $**0.88** = $0.11 x 240 GB x 24 hours/(24 hours x 30-day month)  | $**26.4** = $0.88 x 30 days | 

> ## Your instance incurs **storage cost** while it exists:
>  You need to delete (terminate) your instance to stop incurring storage cost. Storage costs are billed by the second too, with a minimum of 60 seconds. We used hours as the time unit in the calculations above to simplify them but AWS will use seconds to bill your storage cost. 
{: .callout}

### Key management service (KMS) cost
The key management service is related to the login keys you must use to be able to login to your instance. The cost is US $0.03 per 10,000 requests as described in the [AWS Key Management Service Pricing](https://aws.amazon.com/kms/pricing/) page. 

However, KMS is a Free tier *Always free* service with 20,000 requests per month calculated across all Regions that the service is available. Thus only if you exceed 20,000 login requests you will be charged.

### Data transfer (DT) cost
The data transfer service has to do with data you transfer **from your instance** out to somewhere in the Internet including your laptop or desktop, and **into your instance**. You use the DT service when you use the programs `ssh`, `scp`, `curl`, `wget`.

There is **no cost** for **data transfers into** your instance. 

For data you transfer from your instance, DT is a Free tier *Always free* service with "100GB of data transfer out to the internet free each month, aggregated across all AWS Services and Regions (except China and GovCloud)".

Once you exceed the free 100GB, you will be charged as follows:
- US $0.09 per GB for the first 10 TeraBytes (TB) per month, 
- US $0.085 per GB for the next 40 TB per/month
- ... 
 
See more details on the [Amazon EC2 On-Demand Pricing](https://aws.amazon.com/ec2/pricing/on-demand/) page, scrolling down to "Data Trasnfer".

### The total monthly cost of your instance --- no Free Tier
For most practical purposes, we can assume the KMS and DT services are free. You will rarely exceed the Free Tier quotas of these services, 20,000 requests and 100GB.  

Thus the total monthly cost of your instance considering only the EC2 compute cost and the EBS storage cost will be: 

| AMI - instance type - storage size | Compute Cost /day | Compute Cost /month | Storage Cost /month | Total Cost /month |
|---------------|-------------|---------------|---|----| 
| Genomics - t2.micro - 30 GB | $**0.3024** | $**9.072** | $**3.30** | $**12.372** |
| Genomics - t3.small - 30 GB | $**0.5472** | $**16.416** | $**3.30** | $**19.716** |
| Metagenomics - t3.2xlarge - 240 GB | $**8.7552** | $**262.656** | $**26.4** | $**289.056** |


# 2. Free-tier quotas related to your instance
These are the Free Tier quotas that **may** apply to your instance:
- Amazon Elastic Compute Cloud (EC2) --- 12-months free with a monthly quota of 750 hours
- Amazon Elastic Block Storage (EBS) --- 12-months free with a monthly quota of 30 GB-month
- AWS Key Management Service (KMS) --- always-free 20,000 requests per month
- AWS Data Transfer (DT) service --- always-free 100 GB per month

We have already discussed the KMS and DT service quotas in the previous section. 

This section will describe in detail the applicability of the EC2 and EBS service quotas. Briefly, you can only benefit of these service quotas if your instance uses a t2.micro instance type and has up to 30 GB storage. That is, if you created your instance with the Genomics AMI and the t2.micro instance type, **you will not incur any cost** for one year from the time you opened your account.  If you created your instance otherwise (either using a different instance type with the Genomics AMI or using any of the Metagenomics AMIs), **you will incur some cost**.

### The compute service (EC2) Free-tier details

The EC2 Free Tier is described in the [AWS Free Tier](https://aws.amazon.com/free) page ---  scroll down until you see the heading **Free Tier Details** on the left, see the page below (no need to login to your account yet).   

In the page below we have checked the Tier Type filter **12 Months Free** (on the left) and hovered the mouse cursor over the box labelled **Amazon EC2 750 Hours** so that all the information details in the box are uncovered --- we added the two red lines for convenience. 

![Caption.](../fig/02-ec2-free-tier.png "EC2 compute Free Tier details."){: width="900px"}

You can read in that box that: 
1. You have 750 hours **per month**, which amounts to 750/31 days = 24.19 hours for each day in a month. 
2. You can use those hours running **Linux**, **RHLS** (Red Hat Enterprise Linux), and **SLES** (Suse Linux Enterprise Server) with instances of type **t2.micro**, or t3.micro **but only** if t2.micro is not available in the AWS region where you create your instance.  
3. You can have other 750 hours per month to run Windows with instances of type **t2.micro**, or t3.micro but only if t2.micro is not available ..

Clearly, point (1) above means that you can run a t2.micro instance **continuously** until your Free Tier expires without incurring any cost, but see notes below. 

> ## Remember this:
> - The 750 hours for Linux instances cannot be combined with the 750 hours for Windows intances.  
> - The 750 hours for Linux and Windows instances **apply globally to your account**, not to a region and not to an instance. That is, the 750 hours in a month are divided among the number of Linux (or Windows) t2.micro instances that you run in the month in any region. If you run two or more t2.micro instances continuously for one month or longer, you will incur some cost.  
> - Unused hours in a month **do not roll over** to the next month.
{: .callout}

### The storage service (EBS) Free-tier details

To see the details of the EBS Free Tier, scroll further down the AWS Free Tier page until you see the box labelled **Amazon Elastic Block Storage 30GB** and then hover the mouse cursor on the box --- it should look like below:

![Caption.](../fig/03-ebs-free-tier.png "EBS storage Free Tier details."){: width="900px"}

You can see in the page that: (1) you can use up to 30GB of EBS storage for 12 months; (2) EBS storage can be **SSD** (Solid State Drive) storage or magnetic (previous generation) storage with up 2 million Input/Ouput (I/O) operations; and (3) you have up to 1GB of snapshot storage. 

The Genomics AMI uses 30 GB of SSD storage and the Metagenomics AMIs 240 GB of SSD storage. Thus only instances created with the Genomics AMI are Free-tier eligible.

Snapshots are used for backups but your instance does not perform any backups.

> ## Remember this:
> - The Free Tier 30 GBs EBS storage applies to your account. If your instance was created with the Genomics AMI, it is using that many GBs, and you cannot use more storage of any type (SSD or magnetic) without incurring some cost. 
> - Of those 30 GBs in an instance created with the Genomics AMI, 12 GBs are free for data and to install other software applications.
{: .callout}

# 3. Check your service use as compared to Free-tier quotas

AWS bills users **monthly**. Free-Tier eligible services have **monthly** quotas or limits. You must not surpass these quotas in each month if you don't want to incur costs while your Free Tier is active. To find out how much in the current month you have used of your monthly Free-Tier allowance, login to your IAM account and go to the **Billing Dashboard** using the drop-down menu *user@accountalias* (or *user@accountnumber* if you did not create an alias) on the top right. Then, on the navigation pane on the left, under Billing, click on **Free Tier**. A page similar to the one below will apppear.

![Caption.](../fig/05-free-tier-usage-excedeed01Table.png "Free Tier usage summary table.")

The table shows the usage in the current month of each Free-Tier eligible service in your account. For each service, a row in the table shows (from left to right) the type of **Service**, the **AWS Free Tier usage limit**, the service **Current usage** in the month, the service **Forecasted usage** for the month, the service (Month-To-Date) **MTD actual usage** in the month as a percentage of the service monthly Free-Tier limit, and the service **MTD Forecasted usage** for the month. 

**MTD** stands for the period of time between the 1st of the current month and the last finalized day before the current date.

Any service created or used in a month will contribute to the corresponding service usage of the month, even if the service is deleted early in the month.

The first two rows correspond to the **EBS storage** and the **EC2 compute** services presented earlier. Note that EBS storage ("30 GB of Amazon Elastic Block Storage") is reported as being of type *Amazon Elastic Compute Cloud*. The reason is that this storage is *inherent* to your instance: it was created as the root device to hold the software environment (the Cloud-SPAN AMI) of your instance, and, by default, it is deleted when your instance is deleted. You can change this default or deattach the root device before deleting your instance if you want to preserve the storage. Note that there are other types of AWS storage such as S3 (Simple Storage Service) which you can use without attaching them to an instance. S3 is reported as "Simple Storage Service".

The third row corresponds to the login AWS **Key Management Service** which allows you to securely access your instance based on the login key pair you created when you created your instance. The Key Management service is an *always-free* service with up to **20,000 requests free** each month that apply globally to your account. That is plenty of requests. You don't really need to be concerned about it.

The fourth column corresponds to the AWS **Data Transfer** service which allows you to tranfer data **into**, and **out to the internet** from, your instance/s (and other AWS services you may be using). The Data Transfer service is also *always-free* with up to **100 GB free** for *out-to-the-internet* data transfers each month that apply globally to your account.  Data transfers **into** your instance/s (or other AWS services) are **free** --- but you may pay for storing the data; for example, if you transter data into your instance and your Free Tier has expired, you will be paying for EBS storage. 

### **Notes on service usage**

#### **Usage of EBS storage is measured in GB-Month**'s (GB-Mo in the table):
![Caption.](../fig/05-free-tier-usage-excedeed02EBS-row.png "EBS storage Free Tier usage table row.")

GB-Month  is a measure of **how many giga bytes** of EBS storage are provisioned to your account and **how long** the EBS storage is provisioned to your account. It is computed thus:

> ## GB-Month calculation
>
> **GB * usage_hours / hours_in_month**
>
> - *GB* is the size in GBs of the EBS storage.
> - *usage_hours* is the number of hours the EBS storage exists in your account, either provisioned to an instance (running or stopped) or deattached from any instance. You must delete any EBS storage you don't want to add to your billing.
> - *hours_in_month* is the total number of hours in the current month.
{: .callout}

Note that we have used **hours as time unit** in the **formula above** and the **examples below** to simplify the presentation, but you can use minutes or seconds instead of hours in order to get a more precise calculation. AWS uses seconds, see [EBS pricing](https://aws.amazon.com/ebs/pricing/).

Let's see an example of how that formula works for your account assuming you have created only one instance with 30 GBs of EBS storage.

> ## GB-Month calculation example for using 30 GB EBS storage for 1 month and 8 days:
> **Formula**:  30 GB * usage_hours / (days_in month * 24 hours per day)
>
> For **one-month usage** in hours, usage_hours = days_in_month * 24:
>
> in a 30-day month:  30 * 30 * 24 / (30 * 24 ) = 30 GB-Month's\
> in a 31-day month:  30 * 31 * 24 / (31 * 24 ) = 30 GB-Month's\
> in 28-day February: 30 * 28 * 24 / (28 * 24 ) = 30 GB-Month's
>
> For **8-day usage** in hours, usage_hours = 8 * 24:\
> in a 30-day month:  30 * 8 * 24 / (30 * 24 ) = 8 GB-Month's\
> in a 31-day month:  30 * 8 * 24 / (31 * 24 ) = 7.74 GB-Month's\
> in 28-day February: 30 * 8 * 24 / (28 * 24 ) = 8.57 GB-Month's
{: .callout}

You can see that GB-Month measures EBS usage the same for any month regardless of the number of days in the month, but somewhat differently for a given number of days smaller than the number of days for a given month, 8 in the example.

Let's see a billing example assuming your 12-month Free Tier has expired.

> ## Billing example for EBS storage only --- your 12-month Free Tier has expired
> In the Ireland region, the cost of EBS storage is US $ 0.11 per GB-Month (in April 2022).
>
> For the instance your created with 30 GB EBS storage you will pay the following for one month:\
> 0.11 * 30 GB-Month = $ 3.30
>
> If you create and delete your instance (and its EBS storage) after using it for 8 days in a month, you will pay:\
> in a 30-day month:   0.11 * 8 GB-Month = $ 0.88\
> in a 31-day month:   0.11 * 7.74 GB-Month = $0.8514\
> in 28-day February:  0.11 * 8.57 GB-Month = $ 0.9427
{: .callout}

#### **You can use more than 30 GB EBS storage for short periods of time for free**
This is again the first row for EBS storage in the table above:

![Caption.](../fig/05-free-tier-usage-excedeed02EBS-row.png "EBS storage Free Tier usage table row.")

The column **Forecasted usage** shows an **estimate** of total usage of EBS storage for the month based on historical data.  It is an average of usage over a number previous days times the number of days to go in the month --- but we don't know how many previous days are used or if some days usage is weighted.

The forecasted usage in the figure is 32 GB. This is 2 GB more than the 30 GB EBS storage (of the Cloud-SPAN AMI) used to create an instance. Your account should show less than 30 GB, or up to 30 GB of forecasted usage if you only created one instance. The reason for the 2 GB excess in the figure is that we created a second instance which we only used for two days, so we had a total 60 GB of EBS storage in our account for two days, and hence forecasted usage grew accordingly. It went down a few days later after we deleted the two instances we had created.

The relevance of this note is the following. You can see that **Current usage** (in the figure) is only 8 GB despite our using 60 GB for a few days. That means that you can use more EBS storage than the Free-Tier monthly limit, 30 GB, but only for periods of time shorter than a month, for example: 60 GB for about two weeks (half the days in the month), 120 GB for about one week (one fourth of the days in the month), etc. These calculations below show that you would be within the Free-Tier limit:

> ## Using more than 30 GB-Month's within the Free Tier but for less than a month:
> **Formula**: GBs * usage_hours / (days_in month * 24 hours per day)
>
> **60 GB two-weeks usage** (usage_hours = 14 days * 24):\
> in a 30-day month:  60 * 14 * 24 / (30 * 24 ) = 28 GB-Month's\
> in a 31-day month:  60 * 14 * 24 / (31 * 24 ) = 27.10 GB-Month's\
> in 28-day February: 60 * 14 * 24 / (28 * 24 ) = 30 GB-Month's
>
> **120 GB one-week usage** (usage_hours = 7 days * 24):\
> in a 30-day month:  120 * 7 * 24 / (30 * 24 ) =  28 GB-Month's\
> in a 31-day month:  120 * 7 * 24 / (31 * 24 ) =  27.10 GB-Month's\
> in 28-day February: 120 * 7 * 24 / (28 * 24 ) =  30 GB-Month's
{: .callout}

Just recall: *you need to terminate your instance after using more EBS storage than the Free-Tier quota (30 GB) in order not to incur any cost*.

#### **Understanding "MTD actual usage" and "MTD forecasted usage"**

**MTD actual usage** is the total usage of a service in the current month, from the beginning of the month up to the last day before the current date. It is shown in the table as a percentage of the service Free-Tier quota to more easily appreciate how much of that quota has been used. It is computed thus for any service:

*service Current usage / service Free-Tier quota * 100*

Let's compute MTD actual usage for the first three services in the table (shown below):
![Caption.](../fig/05-free-tier-usage-excedeed03EBSnEC2rows.png "EC2 storage Free Tier usage table row.")

> ## MTD actual usage calculations:
> *service Current usage / service Free-Tier quota * 100*
> 
> MTD actual usage EBS =  8 GB-Mo / 30 GB * 100  =  26.6%
>
> MTD actual usage EC2 =  76 hours / 750 hours * 100 = 10.13%
>
> MTD actual usage KMS =  13 requests / 20,000 requests * 100 = 0.065%
{: .callout}

Values of *Current usage* in the table are rounded up or down but *MTD actual usage* values in the table were computed with the non-rounded-up/down values, and hence the slight difference between the *MTD actual usage* values in the table and the values in our example.

**MTD forecasted usage**  is, for each service, the service *Forecasted usage* as a percentage of the service Free-Tier quota, namely:

*service Forecasted usage / service Free-Tier quota * 100*
> ## MTD forecasted usage calculations:
> MTD forecasted usage EBS =  32 GB-Mo / 30 GB * 100  =  106.66%
>
> MTD forecasted usage EC2 =  325 hours / 750 hours * 100 = 43.33%
>
> MTD forecasted usage KMS =  56 requests / 20,000 requests * 100 = 0.27%
{: .callout}

While forecasted usage values in the AWS Free-Tier Summary table (columns 4th and 6th) are only forecasts, you should not ignore them: 

> ## **Remember this**:
> If an **MTD forecasted usage** value in the AWS Free-Tier Summary table has gone **red**, you should do something such as deleting the relevant service or stop using it if you don't want to incur any cost. 
>
> As your instance is created, with the configuration suggested in the previous lesson, it  will not incur any cost even if you don't stop or delete it. You may, however, change its configuration with:
> - more EBS storage or 
> - with an instance type with more capacity
>
> If you add more EBS storage for less than a month, as discussed above, you will need to delete your instance (and hence its EBS storage) for you not to incur any cost. This course does not cover how to increase the EBS storage of your instance but you may find out how to do it in the Internet 
>
> If you use an instance with more capacity for less than a month, you must stop it for some time once you don't need the higher capacity in order not to incur any cost. The calculations to know how much more capacity and for how long you can use without incurring any cost are similar to those shown above for EBS storage.
{: .callout}

# 4. Understanding your bills
AWS bills users every month and the bill of the previous month is available on the 3rd or 4th of the current month. You can access your AWS bills any time in the Billing Dashboard as follows. Login to your IAM account and go to the Billing Dashboard using the drop-down menu **user@accountalias**(or **user@accountnumber** if you did not create an alias) on the top right. Then, on the navigation pane on the left, under Billing, click on **Bills**. A page similar to the one below will apppear.

The page shows a summary of the current month bill (April 2022). At the top, under Bills, the **Date** drop-down menu enables you access previous bills. 

Under "Details - AWS Service Charges", the services being used by our account are shown as drop-down menus and with a cost of $0.00 to the right. Clicking on the drop-down menu of a service will show you the details of usage and cost for the service. 

![Caption.](../fig/06-aws-bill-page01.png "AWS Bills - Example 1.")

In the figure below we have expanded the drop-down menu of the **Elastic Compute Cloud** (EC2) service. Service usage and cost is grouped by region. Our account shows only the Ireland region for EC2 as we are using EC2 in that region only (below is an example showing multiple regions).

Note that we have used 93.542 hours of the EC2 service and 13.549 GB-Month's of the EBS storage service, yet the incurred cost for each service is $0.00 because what we have used of each service so far within the month is within the monthly Free-Tier quota of each service. 

Had our Free Tier expired, the costs shown in the table would be: 
- 93.542 hours *times* $0.0126 USD per hour of t2.micro instance = **$1.178** for the EC2 service so far in the month, and 
- 13.549 GB-Months *times* $0.11 USD per GB-Month = **$1.49** for the EBS storage service so far in the month. 

![Caption.](../fig/06-aws-bill-page02EC2-EBS.png "AWS Bills - Example 2.")

The figure below shows a billing example for EC2 service usage involving two regions and two  (Free-Tier eligible) t2.micro instances and the Free Tier being active but exceeded. Recall that each account has Free-Tier 750 hours per month of t2.micro instance service. 

The **instance** in the Northen Virginia region (1 in red in the figure below) ran for 746 hours in the month with no cost, leaving 750 - 746 = 4 Free-Tier hours still to be used. 

The **instance** in the Oregon region (2) ran for 534 hours. Of these hours, 4 incurred no cost as the 4 Free-Tier hours still to be used were applied. Thus only 530 hours were actually billed for a cost of 530 hours *times* $0.0125 USD per hour of t2.micro instance = **$6.36**.

![Caption.](../fig/07-aws-bill-exceeding-free-tier2.png "AWS Bills - Example 3.")


 

