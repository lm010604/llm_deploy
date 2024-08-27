# LLaMA 3.1 Model Deployment with Ollama

This README provides an overview of the deployment, performance testing, and resource requirements for running LLaMa 3.1 models using Ollama. It also includes guidance on how to set up the necessary environment and optimize the system for handling large language models efficiently.

## Overview
This repository contains scripts and instructions for deploying LLaMa 3.1-8b and LLaMa 3.1-70b models, focusing on performance evaluation under various conditions. The primary goal is to provide practical insights into the GPU configurations and memory requirements needed to run these models effectively, especially in cloud environments.

## Key Features
- Performance Testing: Scripts to evaluate model performance with varying input/output token quantities and concurrent requests.
- Resource Monitoring: Tools to monitor system and GPU utilization during model inference.
- Scalability Guidelines: Recommendations for GPU configurations to optimize performance and cost-effectiveness.

## Table of Contents
- Environment Setup
- Performance Testing
- Results and Analysis
- System and GPU Utilization
- Appendices

## Environment Setup
The following steps outline how to set up your environment for deploying LLaMa 3.1 models using Ollama on Microsoft Azure.

**1. Virtual Machine Configuration:**

- For LLaMa 3.1-8b: Use an instance with an NVIDIA T4 GPU.
- For LLaMa 3.1-70b: Start with an instance with a single NVIDIA A100 GPU. For more intensive tests, consider using dual A100 GPUs.
Virtual Machine Specifications:

Virtual Machine Type | Cores	| RAM	| Disk Size
--- | --- | --- | --- 
Standard_NC4as_T4_v3 | 4 | 	28 GB |	176 GB
Standard_NC24ads_A100_v4 |	24	| 220 GB	| 64 GB

**2. Installing Ollama:** Follow the instructions in Appendix B to install Ollama and set up the models locally.

## Performance Testing

The performance of the LLaMa 3.1 models was tested under various conditions, focusing on two main scenarios:

**1. Output Token Test:**
- **Objective:** Assess how model performance is affected by different output token counts and concurrent requests.
- **Metrics:** Average time to complete a request and average token processing speed.
  
**2. Input Token Test:**
- **Objective:** Evaluate the impact of varying input token counts on model performance with different levels of concurrency.
- **Metrics:** Similar to the output token test, with a focus on the efficiency of input processing.

## Results and Analysis
### Output Token Test
- Both the 8b and 70b models demonstrate a linear increase in request completion time as the output token count rises. However, when the number of concurrent requests increases to four, performance deterioration is more pronounced.
- The average generation speed remains relatively stable with low concurrency but drops significantly when handling four concurrent requests.
### Input Token Test
- The time taken to complete a request increases with higher concurrency, but the impact is less severe compared to output token variations. This suggests that output token generation is more resource-intensive.
### GPU Utilization
- System and GPU utilization metrics indicate that the models are GPU-bound, with memory usage stabilizing at around 42GB for the 70b model during high concurrency tests.
- The LLaMa 3.1 models perform best with sufficient GPU memory, emphasizing the importance of matching GPU resources to model size.

## System and GPU Utilization
- **System Memory:** The system memory requirement aligns closely with the model's size, with no significant overhead observed during concurrent testing.
- **CPU Usage:** CPU utilization is limited, with one core typically handling the bulk of the load. The reason behind this single-core dominance remains unclear.
- **GPU Memory:** GPU memory usage is consistent, indicating that as long as the GPU memory exceeds the model size, it should suffice for deployment.

## Appendices
- **Appendix A:** Detailed specifications of the GPUs used.
- **Appendix B:** Instructions for running LLaMa 3.1 models locally with Ollama.
- **Appendix C:** Python scripts used for performance testing.
- **Appendix D:** Detailed performance data and tables.
- **Appendix E:** Tools and commands for monitoring resource usage.
- **Appendix F:** Additional performance metrics and observations.

## Conclusion
This repository provides comprehensive insights into deploying LLaMa 3.1 models with an emphasis on optimizing GPU resources and understanding the trade-offs involved in handling different workloads. The guidelines and empirical data presented will assist researchers and industry practitioners in making informed decisions, ultimately contributing to more efficient AI deployment strategies.
