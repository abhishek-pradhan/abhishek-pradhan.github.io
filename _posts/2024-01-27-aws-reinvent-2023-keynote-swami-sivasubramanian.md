---
title: AWS re:Invent 2023 Keynote by Swami Sivasubramanian
date: 2024-01-27 14:00
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from ~2 hours of AWS re:Invent 2023 Keynote by Dr. Swami Sivasubramanian, AWS VP Data &amp; ML. 

> New AWS services announced are preceded by (New) &amp; **bold** font
{: .prompt-tip }

## Keynote by Dr. Swami Sivasubramanian, AWS VP Data &amp; ML

### Summary

-  Dr. Swami covered new launches in AWS's AI/ML stack: Amazon Bedrock & Amazon SageMaker and explored how AWS data services are at the core of AI/ML. The focus of the keynote was on Generative AI. Today, there is a powerful symbiotic relationship between Data, Gen AI & Humans which is accelerating our ability to create new innovations & we are just getting started. AWS has everything you need to accelerate your Gen AI journey.

### Highlights

- The Analytical Engine…can follow analysis…but its province is to assist us in making available **what we are already acquainted with** -  **Ada Lovelace**
- More ML workloads run of AWS than any other cloud provider - **HG Insights**
- **Generative AI stack**:
    - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/gen-ai-stack.png)

- **Amazon Bedrock**
    - The easiest way to build & scale gen AI apps on LLMs & other FMs
    - Broad choice of models:
        - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-1.png)
        
        - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-2.png)
        
        - (New) **Models now available in Amazon Bedrock**
            - Anthropic's Claude 2.1
            - Meta's Llama 2 70B
        
    - **Amazon Titan Foundation Models**
        - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-titan.fms.png)
        - Vector Embeddings are numerical representations of text (humans understand text & machines numbers)
            - Vectors are critical for Gen AI apps: VE is helping FMs to produce more relevant response to your search query
            - Amazon Titan Text Embeddings (translates text into numerical representations)
            - (New) **Amazon Titan Multimodal Embeddings**
                - Search, Recommendation & Personalization
                - Accepts text, image, or combination of text-image to generate embeddings
                - Adapts to unique & proprietary data
                - Built-in mitigation to reduce biased search results
        - (New) **Amazon Titan Text Lite** - Summarization, copywriting & ideal for fine-tuning
        - (New) **Amazon Titan Text Express** - Open-ended text generation, conversational chat, RAG support
        - (New) **Amazon Titan Image Generator**
            - Generates Realistic & Studio-quality images 
            - contains invisible watermark inside image for responsible AI
    
    - **Fine-tune** additional models in Amazon Bedrock
        - using your own data & the fine-tuned model remains private & available to you only
        - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-fine-tuning.png)
        - Example: Create Marketing campaign for New product launch - shoes, using Llama 2:
            - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-fine-tuning-example.png)
        - What happens when your price changes or inventory changes, it's not practical to fine tune models each time? Knowledge Bases for Amazon Bedrock launched yesterday, to address this problem:
            - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-knowledge-bases.png)
        - Vector Databases for Amazon Bedrock
            - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/amazon-bedrock-vector-dbs.png)
    
    - AWS Gen AI Innovation Center - accelerating success with tools like Amazon Bedrock - training from AWS

- **Amazon SageMaker**
    - (New) **Amazon SageMaker HyperPod** - Reduces time to train models by up to 40%
    - (New) **Amazon SageMaker Innvoations** - for Inference, Training & MLOps

- A **strong data foundation** is critical to Gen AI
    - A strong data foundation is
        - Comprehensive
        - Integrated
        - Governed
    - A **Comprehensive** set of services for your strong data foundation:
        - ![image](/assets/img/posts/2024-01-27-aws-reinvent-2023-keynote-swami-sivasubramanian/aws-data-services.png)
    - Storing Vectors & Business data speed up Models - **Enabled Vector Search** across AWS services:
        - Amazon Aurora PostgreSQL
        - Amazon RDS for PostgreSQL
        - Amazon OpenSearch Service
        - Amazon OpenSearch Serverless
        - (New) **Amazon DocumentDB**
        - (New) **Amazon DynamoDB**
        - (New) **Amazon MemoryDB for Redis**
    - (New) **Amazon Neptune Analytics**
    - (New) **Amazon OpenSearch Service zero-ETL integration with Amazon S3**
    - Amazon DataZone - Catalog , Discover, Share & Govern Data across Organization
    - AWS Clean Rooms - Create Clean Rooms in minutes & collaborate with your partners, without sharing raw data
    - (New) **AWS Clean Rooms ML** - Apply ML models with your partners without sharing underlying data
    - (New) **AI-driven scaling & optimizations in Amazon Redshift Serverless**
    - Amazon Q - Gen AI powered assistant for your business
    - (New) **Amazon Q generative SQL in Amazon Redshift**
    - (New) **Amazon Q data integration in AWS Glue** - Integrate data using natural language
    - Amazon CodeWhisperer
    - (New) **Model Evaluation on Amazon Bedrock** - Evaluate, compare & select the best FM for your use-case
    - **Survey by World Economic Forum** - Nearly 75% of companies will adopt AI by 2027 
    - AWS Investing in **Educational Programs**:
        - AWS Generative AI Scholarship - Udacity
        - AWS AI & ML Scholarship
        - 100+ AI & ML digital courses
        - (New) **PartyRock** - An Amazon BedRock playground 


## References

- Watch now on YouTube: <a href="https://www.youtube.com/watch?v=8clH7cbnIQw" target="_blank">Keynote by Dr. Swami Sivasubramanian</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/?trk=direct" target="_blank">AWS re:Invent 2022</a>

> Note: Copyrights for images used in this blog post belongs to AWS / Amazon
{: .prompt-info }
