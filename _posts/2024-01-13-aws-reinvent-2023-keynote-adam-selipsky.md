---
title: AWS re:Invent 2023 Keynote by Adam Selipsky
date: 2024-01-13 12:30
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from 1+ hour of AWS re:Invent 2023 Keynote by Adam Selipsky, AWS CEO. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Adam Selipsky, AWS CEO

### Summary

- ReInventing Cloud Computing

### Highlights

- **12th AWS re:Invent** in Las Vegas: 50k+ in-person & 300,000+ attendees registered virtually, over 2200 sessions
- ReInventing Infrastructure:
    - AWS Infrastructure spans **32 Geographical Regions** around the world and each region consists of **atleast 3 AZs**
    - Compared to other cloud providers, AWS has **3x Data Centres, 60% more Services, 40% more Features**
- ReInventing Storage:
    - Amazon S3 (2006 launched)
        - S3 Deep Archive
        - S3 Intelligent-Tier: Saved Customers 2+ Billion dollars
        - New **Amazon S3 Express One Zone**:
            - for high speed storage needs of Customers
            - Highest Performance & Lowest Latency Object storage
            - 10x faster than S3 Standard storage
- ReInventing General Purpose Computing:
    - In 2018, AWS became first major cloud provider to launch GP compute silicon chip - **Graviton**
    - 2020 - Graviton 2 - provides 7x performance than G1
    - 2022 - Graviton 3
        - 25% performance than G2
        - 60% less energy consumption
        - Best price performance in EC2
    - 2023 - New **Graviton 4**
        - Most powerful & energy efficient chip ever made
        - 30% faster than G3
        - 40% faster for DB applications
        - 45% faster for large Java apps
        - Preview of R8g EC2 instances based on G4
- ReInventing with Generative AI
    - **Generative AI stack**
        - ![image](/assets/img/posts/2024-01-13-aws-reinvent-2023-keynote-adam-selipsky/gen-ai-stack-1.jpeg)
        - ![image](/assets/img/posts/2024-01-13-aws-reinvent-2023-keynote-adam-selipsky/gen-ai-stack-2.jpeg)
    - AWS has been collaborating with **Nvidia for 13 years** to bring GPUs to the cloud:
        - ![image](/assets/img/posts/2024-01-13-aws-reinvent-2023-keynote-adam-selipsky/aws-nvidia-collab.jpeg)
        - All GPU instances released in last 6 years is based on AWS Nitro
        - **Jensen Huang - Founder & CEO of Nvidia: Dialog with Adam**
        - New **Nvidia DGX cloud to AWS**
            - DGX cloud is Nvidia's AI factory
    - New **EC2 capacitive blocks for ML**:
        - Reserve EC2 ultra clusters with hundreds of GPUs
        - Ideal for training & fine tuning FMs, short duration workloads & handing capacitive surges
    - **AWS Trainium** - 2nd gen chips launched - 4x faster than 1st gen
    - **AWS Inferentia** - 2nd gen chips launched
    - **AWS Neuron**:
        - SDK to optimize ML on Trainium & Inferentia
        - Supported Frameworks: TensorFlow, PyTorch & upcoming support for JAX
        - Supports 93 of top 100 Models
    - **Amazon SageMaker**: managed service to build, train, deploy ML models at scale
    - **Amazon Bedrock**: easiest way to build & scale Gen AI apps with LLMs & FMs
    - Amazon Bedrock Customization:
        - (New) **Fine Tuning**
        - (New) **Retrieval Augmented Generation (RAG) with Knowledge Bases**
        - (New) **Continued Pre-Training for Titan Text Lite, Titan Text Express**
    - (New) **Agents for Bedrock**
    - (New) **Guard Rails for Bedrock**
    - **Dario Amodei - Anthropic CEO & co-founder: Dialog with Adam**
    - **Amazon Titan Models**: 
        - High performing FMs from Amazon
        - Titan Text Lite, Titan Text Express, Titan Text Embedding model
    - **Lidia Fonseca - Chief Digital & Technology Officer, Pfizer: Speech**
    - Amazon Code Whisperer
    - (New) **Amazon Q**: 
        - Gen AI powered assistant for work, that is tailored for your business
        - Your expert assistant for building on AWS: Currently it has been fed 16 years of AWS docs/ knowledge base and is available in AWS Console & AWS Doc and also in popular IDEs like VS Code
        - Amazon Q Code Transformation: to upgrade code Framework / version, like Java upgrade
            - Coming soon: upgrade DotNet applications to help migrate from Windows to Linux
        - Amazon Q in Quicksight
        - Amazon Q for Amazon Connect
    - Most comprehensive set of Data Services, since your Data is unique & most helpful tool:
        - ![image](/assets/img/posts/2024-01-13-aws-reinvent-2023-keynote-adam-selipsky/aws-data-services.jpeg)
    - Zero ETL Integrations:
        - ![image](/assets/img/posts/2024-01-13-aws-reinvent-2023-keynote-adam-selipsky/zero-etl-integrations.jpeg)
    - Amazon Data Zone
        - Catalog, Discover, Share & Govern Data across your organization
        - (New) **Amazon Data AI Recommendations**
- ReInvent: **Bold bets by Amazon**:
    - Amazon Third Party sellers
    - Amazon Prime
    - AWS
    - Amazon: **project Kuiper**: Global high speed satellite network for broadband / internet connectivity

## References

- Watch now on YouTube: <a href="https://youtu.be/PMfn9_nTDbM?si=NraTQcVO_pPS-l-V" target="_blank">Keynote by Adam Selipsky</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/" target="_blank">AWS re:Invent 2023</a>

> Note: Copyrights for images used in this blog post belongs to AWS / Amazon
{: .prompt-info }