---
title: AWS re:Invent 2022 Keynote by Swami Sivasubramanian
date: 2022-01-16 09:00
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from ~2 hours of AWS re:Invent 2022 Keynote by Swami Sivasubramanian, AWS VP Data &amp; ML. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Swami Sivasubramanian, AWS VP Data &amp; ML

- AWS AI/ML stack:
    ![AWS AI/ML stack](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/AWS-AI-ML-stack.png)
    _AWS AI/ML stack_
- Building an end-to-end Data Strategy:
    ![AWS Building end-to-end Data Strategy](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/AWS-Building-endtoend-data-strategy.png)
    _AWS Building end-to-end Data Strategy_
- New **Amazon Athena for Apache Spark**: Get started with interactive analytics on Apache Spark in under a second
- New **Redshift integration for Apache Spark**: GA - check keynote by Adam
- Apache Spark runs 3x faster on AWS than open source Spark: Customers can run Apache Spark on: EMR, Glue, Sagemaker, Redshift &amp; Athena! 
- New **Amazon DocumentDB Elastic Clusters**: Fully managed solution to scale document workloads of virtually any size &amp; scale
- Amazon SageMaker: 
    - AWS has removed the heavy lifting associated with ML, so that its accessible to many more developers
    - Build, Train &amp; Deploy ML models for any use case with fully managed infrastructure, tools &amp; workflows
    - End-to-end ML Journey: Build -> Train -> Deploy
- Amazon SageMaker **now supports Geospatial ML**: 
    - Making it easier to build, train &amp; deploy ML models using Geospatial data
    - Acquire geospatial data with just a few clicks
    - Easily prepare geospatial data with built-in algos
    - Speed model building with neural network models
- Amazon **Redshift Multi-AZ**: new Multi-AZ feature like RDS
    - Delivering HA &amp; Reliability to support mission-critical Analytics workloads
- New **Trusted Language Extensions for PostgreSQL**:
    - PostgreSQL has hundreds of extensions* available. Customers demanded to have these as managed PostgreSQL Extensions for RDS/Aurora, however they come with security risk of super user access! Due to this AWS introduced Trusted Language Extensions for PostgreSQL:
        - A new **open-source project** to support PostgreSQL extensions on Amazon RDS &amp; Aurora
        - Safely use extensions to meet your needs
        - Install extensions without waiting for AWS certification
        - Leverage popular programming languages
    - * What is PostgreSQL Extension?: 
        - PostgreSQL is designed to be easily extensible &amp; PostgreSQL extensions add extra functionality to your database by modifying and enhancing how it does certain processes.
    - Moreover, Postgres extensions can help with some of the limitations you may find with vanilla Postgres (such as working efficiently with time-series data) – without the hassle of switching to a whole new database.
- New **Amazon Guard Duty RDS protection**: 
    - Protect your data in Aurora with Intelligent Threat Detection
    - Leverages ML to accurately detect suspicious activity
    - Delivers security findings enriched with contextual data
    - Continuously monitors for potential threats with just one click
- **AWS Glue Data Quality**: Automatically measure, monitor &amp; manage data quality in your data lake
- **Centralized Access Controls** for Redshift Data Sharing: Govern access to Redshift using AWS Lake Formation
- ML governance challenges:
    - Creating custom policies is time consuming
    - Capturing &amp; sharing model information can lead to errors
    - Gaining visibility into model performance is expensive
    - To address these challenges:
        - Amazon **SageMaker ML Governance**: Governance &amp; Auditability for end-to-end ML development:
            - Role Manager: Define custom user permissions in minutes
            - Model Cards: Centralize model information &amp; documentation
            - Model Dashboard: Monitor model performance in one place
- New **Amazon DataZone**:  
    - A Data management service to catalog, discover, share, &amp; govern data across organization:
        - AWS Lake formation, Amazon Athena, Amazon RedShift Data sharing, APIs to third-party sources
        - Amazon DataZone is a portal
    - Unlock data across organizational boundaries with built-in governance:
        - Data Producers: Teams that want to share data
        - Data Consumers: Teams that want to use data
        - Amazon DataZone provides unified environment or zone, where everyone in the organization from Data producers to Data consumers can share &amp; access data in a governed manner
        - ![Amazon DataZone 1/4](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/Amazon-DataZone-1.png)
        _Amazon DataZone 1/4_
        
        - ![Amazon DataZone 2/4](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/Amazon-DataZone-2.png)
        _Amazon DataZone 2/4_

        - ![Amazon DataZone 3/4](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/Amazon-DataZone-3.png)
        _Amazon DataZone 3/4_
    
        - ![Amazon DataZone 4/4](/assets/img/posts/2022-01-16-aws-reinvent-2022-keynote-swami-sivasubramanian/Amazon-DataZone-4.png)
        _Amazon DataZone 4/4_

- Amazon **Aurora Zero-ETL integration** with Amazon Redshift
- Amazon **Redshift auto-copy from S3**: Simplify &amp; automate file ingestion into Redshift:
    - Easily create &amp; maintain simple data ingestion pipelines
    - Continuously ingest data as soon as new files are created in S3
    - Automate data loading without engineering resources
- Amazon AppFlow: Move data between SaaS services and data lakes &amp; data warehouses
    - Amazon AppFlow now offer **50+ connectors**
- Amazon SageMaker Data Wrangler: Import data from SaaS services &amp; third-party sources for ML
    - Similarly, access **40+ new data sources** from Amazon SageMaker Data Wrangler
- Education -> Program Update:
    - **AWS ML University** now provides **educator training** (i.e. Train the Trainer): An AI &amp; ML educator training program for community colleges &amp; MSIs in US
    - **AWS AI &amp; ML Scholarship Program** announced last year, 2021 for under-served &amp; under-represented students
    - **150+ courses** from AWS on learning Data &amp; AI/ML

## References

- Watch now on YouTube: <a href="https://www.youtube.com/watch?v=TL2HtX-FmiQ&t=966s" target="_blank">Keynote by Swami Sivasubramanian</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/?trk=direct" target="_blank">AWS re:Invent 2022</a>

> Note: Copyrights for Images used in this blog belongs to AWS / Amazon
{: .prompt-info }
