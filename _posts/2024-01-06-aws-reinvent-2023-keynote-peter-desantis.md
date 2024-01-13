---
title: AWS re:Invent 2023 Keynote by Peter DeSantis
date: 2024-01-06 12:05
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from 1+ hour of AWS re:Invent 2023 Keynote by  Peter DeSantis, AWS SVP, Utility Computing. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Peter DeSantis, AWS SVP, Utility Computing

### Summary:

- Innovations by AWS in Hardware for Serverless computing

### Highlights:

- AWS Serverless offerings (to name a few): Lambda, S3, DynamoDB, Fargate
- Amazon Aurora
    - Fully compatible PostgerSQL & MySQL DBs
    - Biggest innovation of Aurora is internal optimized storage system: powered by **Grover**
        - Aurora sends the log (core of any DB) to Grover, which then writes to multiple AZs!
    - Amazon Aurora Serverless launched in 2018
    - Databases on Nitro hypervisor: however when DB needs more memory, Nitro won't be able to give that, since it would mean to bring down that DB instance & configure a new one with more memory, which is as good as DB failover. Nitro allocates static resources to an instance
        - To avoid this, AWS came up with **Caspian**: Combination of new hypervisor + heat mgmt planning system + few changes to DB engine
            - Caspian allows Aurora Serverless to resize in milli-seconds!
            - Caspian uses an approach called Co-operative oversubscription
            - Caspian can dynamically allocate resources, unlike Nitro
            - ![image](/assets/img/posts/2024-01-06-aws-reinvent-2023-keynote-peter-desantis/caspian-1.png)
            - ![image](/assets/img/posts/2024-01-06-aws-reinvent-2023-keynote-peter-desantis/caspian-2.png)            
    - New **Aurora Limitless Database** 
        - DB Sharding in Serverless world
        - Managed horizontal scale-out beyond the limits of a single instance
        - Innovation 1: New Request Routing Layer
        - Innovation 2: Fully Elastic Shards
        - Innovation 3: Reducing Clock error bounds via Amazon Time Sync Service
- New **Amazon ElastiCache Serverless**
- Amazon Redshift Serverless (launched in 2021)
    - Scales depending on Query Volume
    - New **Next gen AI driven Scaling & Optimization**: to address the challenge by one off massive Query which slow downs rest of the queries
- Quantum Computing:
    - AWS Centre for Quantum Computing established at Caltech in 2019
    - **Quantum computing chip** launched (in prototype)

## References

- Watch now on YouTube: <a href="https://youtu.be/pJG6nmR7XxI?si=8P58ah_gP_SqVsW3" target="_blank">Keynote by Peter DeSantis</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/" target="_blank">AWS re:Invent 2023</a>
