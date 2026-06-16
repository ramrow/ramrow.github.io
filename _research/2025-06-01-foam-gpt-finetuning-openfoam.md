---
title: "Foam-GPT: Fine-Tuning LLMs for OpenFOAM Automation"
category: research_projects
permalink: /research/foam-gpt-finetuning-openfoam/
excerpt: 'My second research project, beginning in Summer 2025 and continuing to the present, focuses on fine-tuning, evaluating, deploying, and improving LLMs that generate OpenFOAM case files for CFD simulation workflows.'
date: 2025-06-01
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/Finetune_research_RPI2025'
---

This is my second research project, beginning in Summer 2025 and continuing to the present. The research focuses on Foam-GPT, an effort to fine-tune large language models so they can generate OpenFOAM input files for computational fluid dynamics workflows. The larger goal is to make an AI agent that can help automate CFD simulation setup by writing valid OpenFOAM files from natural-language requirements.

The project began with [Finetune_research_RPI2025](https://github.com/ramrow/Finetune_research_RPI2025), where I worked with supervised fine-tuning workflows for models such as Llama, Qwen, Mistral, and Granite. I learned and compared multiple fine-tuning toolchains, including LLaMA-Factory, TRL, and Unsloth. This work also introduced me to LoRA, PEFT, quantization, dataset formatting, training configuration, and the tradeoffs between training speed, loss, accuracy, and hardware limits.

A major part of this research was learning how different fine-tuning frameworks behave in practice. TRL gave me lower-level control over the training process and made it easier to inspect the exact training setup. LLaMA-Factory made it faster to configure experiments across multiple models and hyperparameters. Unsloth helped me understand memory-efficient fine-tuning and how quantized or adapter-based training can make larger models practical on limited GPU resources. Across these experiments, I gained hands-on experience tuning model adapters, comparing training runs, and interpreting whether lower training loss actually translated into better OpenFOAM file generation.

After the first round of model training, the research expanded into deployment and evaluation through [foam_standards](https://github.com/ramrow/foam_standards). This repository focuses on benchmarking Foam-Agent 2.0.0 with both open-source and closed-source LLMs. I learned how to deploy models with Ollama and vLLM, configure model runtime providers, run OpenFOAM-based benchmarks, and summarize outputs using success counts, token usage, generated case files, and error patterns. This step was important because fine-tuning alone is not enough; the model has to run in an agent workflow and produce files that pass simulation-oriented checks.

The evaluation work led naturally into [failure_analysis](https://github.com/ramrow/failure_analysis). In that stage, I analyzed why fine-tuned models were still not good enough for reliable OpenFOAM automation. The work included comparing generated outputs against expected files, checking pass/fail results, reviewing file-level differences, and identifying where the model failed: missing required files, producing invalid syntax, generating plausible but incorrect parameters, or failing to preserve the structure expected by Foam-Agent and OpenFOAM. This analysis helped connect model metrics to real engineering usefulness.

To improve the data behind the model, I worked on controlled dataset expansion. In [controlled_dataset_branching](https://github.com/ramrow/controlled_dataset_branching), I used matched OpenFOAM case folders as reusable bases and created controlled velocity variants such as +10%, +20%, and +30%. The pipeline patches OpenFOAM files directly, reruns Foam-Agent validation, and immediately saves accepted dataset rows. This made the dataset more diverse while keeping changes traceable and physically meaningful.

In [controlled_dataset_augmentation](https://github.com/ramrow/controlled_dataset_augmentation), the dataset work expanded into a controlled augmentation ladder. This pipeline creates numeric perturbations for velocity, viscosity, and density, runs each variant through Foam-Agent, and only accepts cases that pass validation checks. I also used Claude through AWS Bedrock for data augmentation and prompt/case generation support, while keeping the output controlled by validation rather than trusting generated data blindly.

As the number of training and augmentation experiments grew, I built tooling for running more experiments in parallel. [slurm_job_manager](https://github.com/ramrow/slurm_job_manager) generates YAML configs and SLURM scripts for learning-rate sweeps, submits jobs with `sbatch`, keeps outputs separated by run, and summarizes results with Weights & Biases. This taught me how to parallelize multiple different trainings on a cluster, manage experiment manifests, organize SLURM outputs, and compare fine-tuning runs efficiently.

Across the project, I learned the full loop of applied LLM research: build and clean the dataset, fine-tune models with LoRA and PEFT, use quantization to fit hardware constraints, deploy models with Ollama or vLLM, evaluate them inside an agent workflow, analyze why they fail, augment the dataset in controlled ways, and scale experiments through SLURM. The project gave me practical experience with both machine learning research and the systems engineering needed to make that research repeatable.

Project repositories:

- [Finetune_research_RPI2025](https://github.com/ramrow/Finetune_research_RPI2025)
- [foam_standards](https://github.com/ramrow/foam_standards)
- [failure_analysis](https://github.com/ramrow/failure_analysis)
- [controlled_dataset_branching](https://github.com/ramrow/controlled_dataset_branching)
- [controlled_dataset_augmentation](https://github.com/ramrow/controlled_dataset_augmentation)
- [slurm_job_manager](https://github.com/ramrow/slurm_job_manager)
