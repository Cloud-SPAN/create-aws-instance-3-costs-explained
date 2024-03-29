---
layout: lesson
root: .
---
The cost of using AWS services depends on:
1. the kind of services used such as compute, storage, networking, etc., 
2. whether the *AWS Free Tier* is applicable, 
3. whether *AWS Cloud Credit for Research* is available, and 
4. the *pricing model* under which services are used.

The *AWS Free Tier* enables you to use **for free** some services within some limits in time and capacity. For example, if you created your instance in the last lesson using the Genomics AMI (30 GB) and the instance type *t2.micro*, your instance will **not** incur any cost during the 12 months from the time you opened your account. In the first episode of this lesson you will learn how to calculate the cost of your instance based on the services it uses, the scope of the AWS Free Tier and the free usage limits that may apply to your instance, how to check your service usage is within the free limits, and how to read your bills. 

The *AWS Cloud Credit for Research*  is credit towards the costs of using AWS services that is available to faculty, researchers and students at an accredited research institution. Student awards can be up to a maximum of US $5,000.00, but the awarded amount will depend on the research project description, the AWS services required, and the cost estimate of service usage as documented in your application. You will learn how to prepare your project and cost estimate to apply for *AWS Cloud Credit for Research* in the second episode.

The pricing model *pay-as-you-go* is the most widely known for cloud computing and is the one that is applied to your AWS service usage by default. Yet AWS offers other pricing schemes which, under some circumstances of service usage, will be cheaper. These include *Savings Plans*, *Reserved Instances*, and *Spot Instances*. These schemes offer from 40% up to 90% discount off *pay-as-you-go* and rely on committing for 1 to 3 years of service usage, or accepting non-immediate (on-demand) service, meaning that your instance may take long to respond or be made unavailable with 2-minutes notice, among other limitations. *Savings Plans* do not apply under AWS Free Tier nor Credit for Research.  And capitalising on *Reserved Instances* and *Spot Instances* requires more involved configuration of AWS services and your applications. For these reasons, we will not consider these other pricing models any further in the remainder of this lesson. We will only consider the *pay-as-you-go* model from now on. 

