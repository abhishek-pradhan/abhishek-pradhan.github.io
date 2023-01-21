---
title: AWS re:Invent 2022 Keynote by Werner Vogels
date: 2023-01-08 12:10
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from ~2 hours of AWS re:Invent 2022 Keynote by  Dr. Werner Vogels, Amazon CTO. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Dr. Werner Vogels, Amazon CTO

- Key message: **Nature is Asynchronous**, World is event-driven &amp; hence our systems should be as well! 
    - S3 Design Principles (based on Distributed systems): Decentralization, **Asynchrony**, Local responsibility, **Decompose** into small well-understood building blocks, Autonomy, **Controlled concurrency**, Failure tolerance, **Controlled parallelism**, Symmetry, Simplicity 
    - Asynchrony leads to loosely coupled systems 
    - Benefits of loosely coupled systems: Fewer dependencies, Failure isolation, Evolvable architecture 
    - Evolvable architecture:  S3 when launched had 8 microservices &amp; now it has 253+ svcs! 
    - Amazon.com architecture: Monolith -> SOA -> MSA -> Shared services (read Amazon's Distributed computing manifesto,1998 from Werner's blog) 
- New **AWS Step Functions Distributed Map**: serverless Map &amp; Reduce using Lambda functions 
- Event Bridge supports all 3 Event driven patterns: 
    - Point to Point using Queue 
    - Publish / Subscribe using Broker 
    - Event Streaming using Broker 
- Readme.com to create docs for APIs 
- New **AWS Application Composer**: Visually build &amp; design Serverless Apps quickly 
- Spider in the Web  (where Spider is central thing)-> EventBridge: 
    - EventBridge does Routing, Coordination &amp; Scheudling 
    - New **Amazon EventBridge Pipes**: Connects event producers &amp; consumers in seconds (i.e. Stich AWS services together like Unix Pipes) 
- Design patterns used in DynamoDB Global tables that can be used in any global app: 
    - Change Data Capture 
    - Asynchronous Coupling 
    - Self healing replicator 
- Check out Amazon Builders Library for design patterns 
- New **Amazon Code Catalyst**: 
    - A unified software development service that makes it faster to build &amp; deliver in AWS (it has all the tools you need to go from idea to production)
    - It's basic concept is of **blueprint** (like SPA application)
    - It let's you easily create CI/CD pipelines, Development environments (to easily switch between codebases in 1 click)
    - CodeCatalyst service seems similar to Azure DevOps
- Gaming: 
    - Unreal Engine 
    - AWS Ambit Scenario Designer 
- Experiment, Measure, Learn! 
- New **AWS SimSpace Weaver**: Runs massive spatial simulation 

## References

- Watch now on YouTube: <a href="https://www.youtube.com/watch?v=RfvL_423a-I" target="_blank">Keynote by Werner Vogels</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/?trk=direct" target="_blank">AWS re:Invent 2022</a>
