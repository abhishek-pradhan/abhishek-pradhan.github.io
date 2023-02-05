---
title: AWS re:Invent 2022 Keynote by Peter DeSantis
date: 2023-02-05 12:30
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from 1+ hour of AWS re:Invent 2022 Keynote by  Peter DeSantis, AWS SVP, Utility Computing. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Peter DeSantis, AWS SVP, Utility Computing

- AWS Nitro silicon chip:
    - AWS Nitro architecture:
        - Server = customer instance
        - Hypervisor
        - Beneath is Nitro Controller = Networking, Storage, Management security & monitoring
        - Every new EC2 instance introduced since 2014 has Nitro Controller!
    - New **AWS Nitro v5 chip** launched GA:
        - v5 is Arm based architecture, 2x transistors (means twice the computation), 50% memory bandwidth, 2x PCIe bandwidth
        - New EC2 instance based on v5 = C7gn (Graviton based EC2)
        - New EC2 instance for HPC = HPC7g
- Network topology:
    - Traditional networking based on TCP connection = Single Path through Network
    - **SRD** = Multi-path through Network (under the hood it uses TCP!), Retries in ms, Runs on Nitro whereas TCP uses Guest operating system!
        - Due to above factors SRD provides Lower Latency & Higher Throughput and is used for EFA (HPC), EBS (storage), ENA (networking)
        - Coming soon - All new EBS io2 volumes will be running on SRD
        - Elastic Network Adapter (ENA) - Default network interface for Amazon EC2
            - ENA Express - bringing SRD to mainstream
- ML: Training performance of Neural Network Models:
    - **Stochastic Rounding** resulted in fast convergence as compared to 32 bit or  16 bit or Mixed precision
    - Upto 75% Faster synchronization with Ring of Rings algo
    - New **Trn1n** (Trainium) based EC2 instances - coming soon
- Serverless computing:
    - AWS Lambda: launched in 2014 - first serverless computing service 
        - From t2 EC2 instance per Lambda function to FireCracker (micro-VM) to avoid Cold start (reduced by 50%)
        - Cold start occurs due to Compute Cache Hits
        - New **Lambda SnapStart for Java**: significantly reduces Lambda function cold start latency, at no extra cost - in GA
            - Upto 90% reduction in cold start latency
            - Initialization snaphot taking for JVM & used across different Lambda functions!
            - No code change required, just enable for new or existing Java Lambda
- Ferrari Racing session by Jock Clear

## References

- Watch now on YouTube: <a href="https://www.youtube.com/watch?v=R11YgBEZzqE" target="_blank">Keynote by Peter DeSantis</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/?trk=direct" target="_blank">AWS re:Invent 2022</a>
