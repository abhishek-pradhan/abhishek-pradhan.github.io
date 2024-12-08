---
title: AWS re:Invent 2024 Keynote by Peter DeSantis
date: 2024-12-08 10:00
categories: [AWS, re:Invent, Keynote]
tags: [aws, reinvent]
render_with_liquid: false
---

Here I have captured key highlights from 1+ hour of AWS re:Invent 2024 Keynote by  Peter DeSantis, AWS SVP, Utility Computing. 

> New AWS services announced are preceded by New &amp; **bold** font
{: .prompt-tip }

## Keynote by Peter DeSantis, AWS SVP, Utility Computing

### Summary

Focus was majorly on:
1. How Graviton chipset along with Nitro helped AWS renovate at Serve Hardware layer.
1. Launch of new Trainium2 chipset & purpose built network '10p10u' & network routing for AI and it's benefits for running AI workloads in AWS

### Highlights

Peter DeSantis's keynote wasn't just about showcasing new products; it was about illustrating **how AWS thinks and operates**. He used the analogy of a tree to highlight the intricate connection between AWS's visible innovations (the "trees") and the less obvious but equally critical foundational elements (the "roots") that fuel their success.

![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/summary.jpg)

#### Dave Brown: The Silicon Revolution

Dave Brown, VP of Compute and Networking, took the stage to elaborate on AWS's groundbreaking work with custom silicon. He highlighted:

- **The Graviton Journey:** Brown charted the evolution of AWS's Graviton processors, emphasizing their focus on real-world performance benefits for customers. He explained how each generation of Graviton has delivered substantial improvements, culminating in Graviton4, their most powerful chip yet. He showcased how Graviton consistently outperforms traditional benchmarks in real-world applications like NGINX and MySQL.
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/graviton-generational-improvements.png)
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/graviton-powered-aws-services.png)

- **Nitro: Redefining Server Architecture:** Brown explained how the Nitro System has become a cornerstone of AWS's infrastructure, driving security and agility. He emphasized Nitro's role in establishing a cryptographically secure chain of custody for hardware, ensuring the integrity of every component from manufacturing to operation.
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/aws-nitro-system.png)

- **Disaggregated Storage: Breaking Free From Constraints:** Brown detailed how AWS leverages Nitro to decouple compute and storage, creating a more flexible and resilient architecture. This disaggregation enables independent scaling of resources, reduces blast radius in case of failures, and simplifies maintenance. He used the example of "Barge", a previous high-density storage server, to highlight the limitations of tightly coupled systems and the advantages of disaggregation.
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/disaggregated-storage.png)

#### Peter DeSantis: The Rise of AI: Scaling Up and Out

DeSantis returned to discuss the rapidly growing field of AI, noting its unique demands on infrastructure. He explained how the rapid growth of AI models, driven by the **"Scaling Laws"**, necessitates a two-pronged approach: (1) **scaling up** individual server power and (2) **scaling out** clusters for distributed training.
![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-scale-up-scale-out.png)


- **The Scale-Up Challenge: Trainium2 Unveiled:** DeSantis introduced New **Trainium2**, AWS's answer to the scale-up challenge. He walked the audience through the intricate engineering behind this powerful AI server, highlighting the use of **Advanced Packaging**, techniques to minimize voltage drop, and the benefits of automated manufacturing. He delved into Trainium2's **Systolic Array Architecture**, a unique approach that optimizes data flow and memory bandwidth utilization for AI workloads & due to thsi architecture how Trainium is different from CPU & GPU chips!
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-trainium2-advance-packaging.png)
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-trainium2-systolic-array-architecture.png)    

- **NeuronLink and UltraServers: Pushing the Boundaries:** DeSantis showcased **NeuronLink**, a proprietary interconnect technology that enables multiple Trainium2 servers to function as a single, immensely powerful unit called an **UltraServer**. This innovation enables the training of truly massive AI models.
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-trainium2-neuron-link.png)
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-trainium2-ultraserver.png)    

- **The Scale-Out Challenge: Building a Supercharged Network:** DeSantis emphasized that building powerful AI servers is only half the battle.  Training large models requires vast clusters, and that necessitates an incredibly robust and scalable network. He drew parallels between the requirements of cloud networks and the even more demanding needs of AI networks, highlighting the need for massive capacity, rapid scalability, and extreme reliability.

- **The 10p10u Network: A Network Built for AI:** DeSantis introduced the New **10p10u network**, AWS's custom-built, high-performance network fabric specifically designed for AI workloads. He highlighted its massive capacity, elasticity, and the innovations that have enabled its rapid scaling, including trunk connectors and the Firefly Optic Plug.

- **SIDR:  A New Era of Network Routing:** DeSantis explained how AWS developed SIDR, a novel network routing protocol that combines centralized planning with decentralized execution, enabling the 10p10u network to respond to failures with lightning speed.

- New **Latency-optimized Inference option for Amazon Bedrock** introduced in Preview & it's performance gains on Llama 3.1 on Trainium2
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-bedrock-latency-optimized-inference-option.png)
    - ![image](/assets/img/posts/2024-12-08-aws-reinvent-2024-keynote-peter-desantis/ai-bedrock-latency-optimized-inference-option-llama3.1-performance.png)    

#### Tom Brown:  The Power of Partnership

Tom Brown of Anthropic joined DeSantis to discuss their collaboration in leveraging AWS's AI infrastructure to build and deploy Claude, Anthropic's cutting-edge AI assistant.  

- **Claude 3.5 Haiku: Speed and Efficiency on Trainium2:** Brown highlighted the significant performance gains achieved by running Claude 3.5 Haiku on Trainium2. He explained how this latency-optimized version is ideal for interactive applications and showcased the collaboration between Anthropic and AWS in developing low-level kernels to maximize Trainium's performance.

- **Project Rainier:  A Glimpse into the Future:** Brown announced Project Rainier, a massive new Amazon cluster powered by hundreds of thousands of Trainium2 chips dedicated to Anthropic's next generation of AI models. This partnership exemplifies the power of collaboration in pushing the boundaries of AI innovation.

## References

- Watch now on YouTube: <a href="https://www.youtube.com/watch?v=vx36tyJ47ps" target="_blank">Keynote by Peter DeSantis</a>

- Explore: <a href="https://reinvent.awsevents.com/keynotes/" target="_blank">AWS re:Invent 2024</a>

> Note: Copyrights for images used in this blog post belongs to AWS / Amazon
{: .prompt-info }