---
title: "The AWS Cloud Credit for Research"
teaching: 20
exercises: 10
questions:
- "What is the AWS Cloud Credit for Research programme?"
- "Who can apply?"
- "How to apply?"
objectives:
- Know the scope and benefits of the AWS Cloud Credit for Research programme.
- Understand the requirements and process to apply to this programme.
- Get acquainted with structure of the project you need to submit with your application.
- Learn how to get the cost estimate of your project.
keypoints:
- AWS Cloud Credit for Research is open to graduate, posgraduate and PhD students at an accredited institution.
- To apply you need to submit a project which requires some planning.
- You need to open your AWS account to which the award promotional credit is applied.
---
> ## Prerequisites
> You need to read the previous episode [The AWS Free Tier](../01-free-tier) for you to be able to follow the third part of this episode.
{: .prereq}

# Introduction
> This episode provides an overview of these topics:
>
> 1. [**The AWS Cloud Credit for Research (ACCR) programme**](#1-the-aws-cloud-credit-for-research-accr-programme)\
You will learn about the types of projects supported by ACCR, eligibility criteria, awards and scope, and the application process.
>
> 2. [**Preparing your application to ACCR**](#2-preparing-your-application-to-accr).\
You will learn the structure of your research project as expected by AWS and the evaluation criteria for you to organise your project content accordingly.
>
> 3. [**Getting the cost estimate of your project**](#3-getting-the-cost-estimate-of-your-project).\
This section will show you how to get the cost estimate of your project which you must include with your application.
{: .callout}

# 1. The AWS Cloud Credit for Research (ACCR) programme
[ACCR](https://aws.amazon.com/government-education/research-and-technical-computing/cloud-credit-for-research/) supports the public sector in the adoption of cloud technologies under research and training projects. It provides funding in the form of credit that can only be used to pay for the cost of using AWS services under such projects. 

### Types of projects
The type of projects considered under ACCR include:

- *Proof of concept or benchmark tests*:\
That evaluate the efficacy of moving research workloads or open data sets to the cloud.

- *Development of repeatable, sharable solutions*:\
That build cloud-hosted publicly available science-as-a-service applications, software, or tools to facilitate a community's future research.

- *Advanced workshops or tutorials*:\
That train a broader community on the use of cloud for research workloads.

ACRC "does **not** support administrative workloads, operational projects, or ongoing projects".

### Eligibility
ACRC is open to full-time faculty, full-time researchers, and students at an accredited research institution. Graduate, post-graduate and PhD students are eligible. ACCR is intented for relatively long (up to one year), research-oriented projects. Student awards can be up to a maximum of US $5,000.00 --- faculty and researcher awards have no limit.

If you want to learn cloud skills rather than conduct research, the [AWS Educate](https://aws.amazon.com/education/awseducate/) is a free programme available to everyone.

### Awards and scope

The awarded amount will depend on the research proposal and AWS service  requirements in your application. An award is referred to as **AWS Promotional Credit** or **Promotional Credit**.  The Promotional Credit you receive may be **less** than you applied for. 

Promotional credit **has some restrictions in use**. Usage of EC2 services is **only covered** under the pricing schemes *pay-as-you-go* (also known as *on-demand*) and *Spot Instances* only and **cannot be used** to pay for **previous charges**. 

Please see other restrictions and guidelines in the [AWS Promotional Credit Terms & Conditions](https://aws.amazon.com/awscredits/).

### The application process at a glance

You will be informed of the **the outcome of your application** in an email from **aws-research-credit@amazon.com** (check your spam folders) within 120 days but often much sooner. 

If your application is successful, you will receive Promotional Credit directly applied to your AWS account or an email with a *Promotion Code* to redeem in your account on the **Billing Dashbord**. 

If your application is **not** successful, you can submit **revised** application


### Other points you should know

**Acknowledgements**:\
You should acknowledge your ACCR award as "AWS Cloud Credit for Research" in any outcome of your project.

**How long is Promotional Credit valid?**:\
Promotional Credit expires after one year from the time it is applied to your account or until it is used entirely. Any promotional credit not used after the expiration date is forfeited. Once any of these conditions happen, **your credit card will be charged** for any AWS services you use. Check your credit regularly or set Billing Alerts through the Billing Dashboard.

**You can submit another application for the same project**:\
If your project runs for longer than planned, you can apply for another ACCR award explaining your project progress and including any outcomes and milestones you have reached.

# 2. Preparing your application to ACCR

To apply for an ACCR award, you will fill and submit the online application form here: [ACRC Application Details](https://pages.awscloud.com/aws-cloud-credit-for-research.html). You will need:

- An AWS account --- you will need to enter your 12-digit account number 
- a research project description --- guidelines below
- a Faculty Advisor --- you will need to give their name
- an institution email address
- a phone number

### Writing your research project

Your research project must include the following (from [ACRC Application Details](https://pages.awscloud.com/aws-cloud-credit-for-research.html)):

1. Description of problem to be solved.
2. Proposed Amazon Web Services (AWS) solution (including specific AWS tools, timeline, key milestones).
3. Plan for sharing outcomes (tools, data, and/or resources) created during project.
4. Any potential future use of AWS beyond grant duration by individual research group or broader community.
5. Names of any AWS employees you have been in contact with (this is not a prerequisite for the application).
6. Any AWS Public Data Sets to be used in your research.
7. Keywords to facilitate proposal review.

In preparing your application you should consider [Factors AWS considers to determine who receice Promotional Credit](https://aws.amazon.com/government-education/research-and-technical-computing/cloud-credit-for-research/faqs/proposal-preparation/).

### Filling the application form

All fields in the ACCR application form are **required** and the filling of most of them is straightforward.

However, the following two fields require preparation:
- *Save and Share URL from AWS Pricing Calculator*
- *Project Description*

![Caption.](../fig/aws-credit4research/02-accr-application-form-cost-url-project-description.png "The ACCR form with the 'Save and Share URL from AWS Pricing Calculator' and 'Project Description' highlighted"){: width="900px"} 

The field *Save and Share URL from AWS Pricing Calculator* requires that you enter the URL of the cost estimate of your project. You need to prepare it with the [AWS Pricing Calculator](https://calculator.aws/#/) --- civered in the next topic "3. Getting the cost estimate of your project".

We recommend preparing the *Project Description* in a plain text editor (**not** Word) before pasting it into the box. 

# 3. Getting the cost estimate of your project

To get the cost estimate you will need a list of services and the estimated "capacity" of each", that you need. You enter these in the AWS Pricing Calculator. Your estimate of the *capacity* (not cost) of each service and the configuration you choose for the service do not have to be precise. 

### Cost estimate example

Let's suppose the following: 
1. You created your instance as suggested in the lesson [Create and Manage your AWS instance](https://cloud-span.github.io/create-aws-instance-2-manage-instance/) so that it is Free-Tier eligible, that is: you created an instance of type *t2.micro* (with 1 processor and 1 GB memory) and 30 GB Elastic Block Storage (EBS). 
2. You have used your instance for a few weeks and found that some of your programs take too long to finish and you would like to process a larger data set that you need to transfer into your instance storage
3. You want to apply for ACCR Promotional Credit to upgrade your instance to be of type *t2.medium* (2 processors and 4 GB memory) and 120 GB storage.  

Thus, we are going to get a cost estimate for an EC2 instance t2.medium and 120 GB EBS storage. 

You may recall that, when you use your instance, you also use the *Key Management Service* (KMS) and the *Data Transer* (DT) service, both of which are *always-free* services with 20,000 free requests per month  and 100 free GB per month respectively. In this example, we assume those always-free monthly quotas will be enough for your project but if you think you nee more, you can include them in your cost estimate as described below.

### Getting the cost estimate and its URL

Go to the page of the [AWS Pricing Calculator](https://calculator.aws/#/) --- you do **not** need to login to your account to access the pricing calculator.

Once the AWS Pricing Calculator page appears, click on **Create estimate** and the "Select service" page will appear. 

Type **ec2** in the search box to display only the services whose name contain EC2. The service we are interested in is the first one: "Amazon EC2". In the "Amazon EC2" box, click **Configure**.

![Caption.](../fig/aws-credit4research/03-accr-pricing-calculator-ec2.png "AWS Pricing Calculator showing the 'Select service' page with 'ec2' typed in the search box and the 'Amazon EC2' service listed first"){: width="900px"} 

The "Configure Amazon EC2" page will appear. Select the box "Advance estimate" and then scroll down until you see the heading "EC2 Instances". Continue below.
![Caption.](../fig/aws-credit4research/04-accr-pricing-calculator-ec2-advEstimate.png "The 'Configure Amazon EC2' with 'Advanced estimate' selected."){: width="900px"} 

Type "t2.medium" in the "EC2 Instances (1)" search box. This will then list "t2.medium --- 4 GiB --- etc" in the table. Select this row.

![Caption.](../fig/aws-credit4research/05-accr-pricing-calculator-ec2-t2.medium.png "The 'EC2 Instances (1)' search box showing 't2.medium' typed in and the 't2.medium --- 4 GiB --- etc' listed in the table."){: width="900px"} 

Scroll down to "Pricing strategy" and select "On-Demand".

![Caption.](../fig/aws-credit4research/06-accr-pricing-calculator-ec2-pricing-model.png "'Pricing Strategy' showing 'On-Demand' selected"){: width="900px"} 

Scroll down again to "Amazon Elastic Block Storage (EBS)", enter 120 in "Storage amount" and set "Snapshot Frequency" to "No snapshot storage".

![Caption.](../fig/aws-credit4research/07-accr-pricing-calculator-ec2-120EBS.png "'Amazon Elastic Block Storage (EBS)' showing 120 in 'Storage amount' and 'Snapshot Frequency' set to 'No snapshot storage'."){: width="900px"} 

Scroll to the end of page to see your "Amazon EC2 estimate". This is the *monthly* fee for each service and the total for both services in US dollars. Click on "Add to my estimate"

![Caption.](../fig/aws-credit4research/08-accr-pricing-calculator-total-monthly-estimate.png "The Monthly cost estimate."){: width="900px"} 

The page will now show your cost estimate for 12 months at the top, and the details of your instance configuration below: Ireland region, intance type t2.medium, 120 EBS storage, On-Demand Pricing strategy.

Note the options at the top: **Add service**, **Add support**, .., and **Share**.

In this example, we do not need to add any services but you could add more using **Add service**. You can create as many cost estimates as you want. They are deleted after three years. 

![Caption.](../fig/aws-credit4research/09-accr-pricing-calculator-annual-estimate.png "The Annual cost estimate."){: width="900px"} 

**Share** is what you need for your application. Click on **Share**

You will then be asked to **Agree and continue** to save your cost estimate and given the opportunity to **Copy public link** to the estimate. This is the URL you need for your application.

You can now complete you application!