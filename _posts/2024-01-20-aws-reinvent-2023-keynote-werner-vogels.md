---
title: AWS re:Invent 2023 Keynote by Werner Vogels
date: 2024-01-20 14:00
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from ~2 hours of AWS re:Invent 2023 Keynote by Dr. Werner Vogels, Amazon CTO. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Dr. Werner Vogels, Amazon CTO

### Summary

-  Matrix movie-styled theme where Dr. Werner (as Neo) advised the Architect to be Frugal Architect by keeping Cost in mind (from the beginning), while designing systems & cloud migration. Dr. Werner also explains AI's evolution and how easy it is for a builder to use AWS's AI services when designing systems & the impact it will have  in our world.

### Highlights

- On-Premises always had Hardware constraints, whereas Cloud removed these constraints. However, since most are already in Cloud and not experienced On-Premises & its constraints, we have forgotten the art of Architecting for cost.
- **Architect with cost in mind** - Werner - AWS re:Invent 2012
- **PBS** - reduced their streaming cost by 80%, by migrating to AWS in 2009 and over period of time re-architected their workloads by using as many AWS services as possible
- **Sustainability** 
    - Next to Cost, that is something on my mind these days & should be on yours as well
    - Cost is a close proxy for Sustainability
    - Through-out this keynote, when I say Cost, also keep Sustainability in mind
- **WeTransfer** - 78% reduction in the emissions from server use in 2022
- **The Frugal Architect**: Observations (Laws) by Dr. Werner, while working as Amazon CTO for 20 years now:
    - ![image](/assets/img/posts/2024-01-20-aws-reinvent-2023-keynote-werner-vogels/frugal-architect-1.png)
    - **Design**
        1. Cost is a Non-Functional Requirement (NFR) - Consider Cost at every step of your design
            - Example: When designing S3, this is how costing was handled: Customers are charged for Storage, Bytes Transferred, Number of Requests
            - Example: When designing DynamoDB, this is how costing was handled: Customers are charged twice for Strong Consistency Reads than Eventual Consistency Reads
        1. Systems that last align Cost to Business
            - Align Cost & Revenue: Pay off your debts
            - **Flywheel Effect** by Jeff Bezos - Business decisions & Technology decisions should be in Harmony with each other
            - Example: Lambda costing: Charged over 2 dimensions: ms of CPU used & amount of Memory used, but initially AWS took the cost on self, instead of Customers - this was the debt that had to be paid, so they created Firecracker.
                - **Firecracker**: MicroVMs based on KVM
                    - invented to reduce the cost hits that AWS was taking initially on Lambda, as Lambda's cost was taken on AWS, instead of the customers.
                    - Without Firecracker, AWS wouldn’t be able to invent Fargate!
                    - Build Evolvable Architecture, because architectures change over time: Initially Lambda was using T2 EC2 instances for running Lambdas, now its on Firecracker. AWS made this switch internally without customers knowing about it!
        1. Architecting is a Series of Trade-offs
            - Series of Trade-offs between Non-functional requirements & Functional requirements
            - Remember, every Engineering decision is a Cost decision
    - **Measure**
        1. Un-observed Systems lead to Unknown Costs: Define your meter
            - Case study: Amazon.com consists of x-number of microservices & pages, so measure costs at microservices & UI, like Cost / Request at Microservice level, Transitive Cost / Request at System level:
                - Cost / Request at Microservice level: Most importantly, your cost should be going down - by profiling / re-architecting app / moving to Graviton 
                - Transitive Cost / Request at System level: What's the cost of serving this application or webpage
                - Conversion rate / Request = Products Sold / page views
            - New **AWS Management Console myApplications**
                - Monitor & manage the Cost, Health, Security posture & Performance of your applications
            - New **CloudWatch Application Signals**
                - Automatically instrument & operate applications to track application performance against your most important business objectives
        1. Cost-aware architectures implement Cost-controls: Establish your Tiers
            - Decompose parts of your app into Tiers (from most important to least for Business) - Tiers inform Trade-offs - You can now scale as per these Tiers & manage costs
    - **Optimize**
        1. Cost Optimization is Incremental: Continuously Optimize 
            - Eliminate Digital Waste: Use tools like language profiler or AWS CodeGuru Profiler to find out waste
                - Savings Opportunities: Stop, Right-size, Shift, Reduce 
        1. Unchallenged Success leads to Assumptions: Disconfirm your beliefs, put your ego aside
            - **The most dangerous phrase in English: "We have always done it this way…" - Rear Admiral Grace Hopper**
                - We are a Java shop - Java developer, 2019
                - We are great at Ruby - Ruby on Rails dev, 2017
                - We have done this before (in my previous company) - Startup CEO, 2012
            - Cost to Build dwarfs Cost to Operate, i.e. Cost to Build < Cost to Operate 
            - Ranking Programming languages by Energy efficiency - Rui Pereira, INSEC Tec, Portugal:
                - Ruby & Python are more than 50x expensive as that C++ & Rust
                - ![image](/assets/img/posts/2024-01-20-aws-reinvent-2023-keynote-werner-vogels/ranking-programming-languages-by-energy-efficiency.png)
    - https://thefrugalarchitect.com/
    - ![image](/assets/img/posts/2024-01-20-aws-reinvent-2023-keynote-werner-vogels/frugal-architect-2.png)


- **Artificial Intelligence (AI)**
    - **"I propose to consider the question, Can machines think?" - Alan Turing**, Computing Machinery & Intelligence, 1950
    - **Symbolic AI** (top-down approach)
        - Can we implement reasoning?
        - Implemented using Expert systems - which incorporated knowledge in rules & they can execute queries against it and got back answers, but were laborious & weren't terribly smart
    - **Big breakthrough** came when we shifted from **Symbolic AI** (top-down) to **Embodied AI** (bottom-up)
    - **Embodied AI** (bottom-up approach)
        - Can we create basic building blocks, like tasks that humans performed? May be out of that, we can build AI
        - Mostly driven by an idea of having Robots. Can we give sensors that humans have, like Speech recognition, image recognition & may be sensors like humans don't have like LIDAR to Robots?
        - This thinking has driven us for past 10-15 years & resulted into new Algorithms
            - Deep Learning
            - Re-enforcement Learning
        - Next revolution in AI is **Transformers**
            - Ability to use Transforms to build **Foundational Models (FMs)** & **Large Language Models (LLMs)**
        - However, not all use-cases requires new AI, there are use cases for good old AI too
            - **International Rice Research Institute (IRRI)** in Manila uses Vision Management to sort rice samples sent to them to determine which seeds should go to seed bank
            - **Cergenx** in Ireland uses Sagemaker to determine via EEGs, if new born babies have brain injuries (which normally gets detected after couple of months) thereby improving Quality of Life
            - **Precision.AI** are using Autonomous Drones & has a task to avoid the complete plot of lands that are sprayed with chemicals to remove weeds
            - **Digital Earth**, Africa make use of open dataset of satellite imagery of Africa and many governments use this to identify issues like monitoring coastal erosion in Zanzibar, identify the impact of illegal mining in Ghana and identify forest fires in South Africa & Kenya
        - All of the above is based on availability of good data sets. **Without good Data, there is no good AI!**
        - **ML is the magnet** to find needle in the haystack (tons of data)
        - Dr Warner built end to end system leveraging ML model using AWS SageMaker (over 5 weekends) to detect brain haemorrhage (stroke):
            - ML University: https://aws.amazon.com/machine-learning/mlu/
            - Intracranial Hemorrhage Detection for Radiologist Workflow Prioritization: https://github.com/aws-samples/radiology-worklist-ich-detection
        - **Al predicts, Professionals decide!** - AI is assistant, they don't make decisions for you
    - New **Amazon SageMaker Studio Code Editor** - based on open source VS Code
    - Preview **Amazon Q** in your IDE like VS Code
    - New **AWS Application Composer in VS Code** - Visually compose Infrastructure as code directly in VS Code
    - New **Amazon Inspector CI/CD Container Scanning** - Enhancing container image security with Amazon Inspector integration with developer tools

## References

- Watch now on YouTube: <a href="https://youtu.be/UTRBVPvzt9w?si=TLLkG063_ehnOPld" target="_blank">Keynote by Werner Vogels</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/?trk=direct" target="_blank">AWS re:Invent 2023</a>

- Read: <a href="https://thefrugalarchitect.com/" target="_blank">The Frugal Architect</a>

- Learn: <a href="https://aws.amazon.com/machine-learning/mlu/" target="_blank">ML University</a>

- Code: <a href="https://github.com/aws-samples/radiology-worklist-ich-detection" target="_blank">ML Model to detect brain haemorrhage (stroke)</a>

> Note: Copyrights for images used in this blog post belongs to AWS / Amazon
{: .prompt-info }