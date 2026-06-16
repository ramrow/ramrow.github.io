---
title: "SLURM Job Manager for Fine-Tuning Experiments"
category: research_projects
permalink: /research/slurm-job-manager/
excerpt: >
  This repository helped scale the research by parallelizing many fine-tuning experiments on a cluster. I learned SLURM scripting, sbatch job submission, experiment manifests, training sweep organization, and result tracking for faster model iteration.
date: 2025-06-06
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/slurm_job_manager'
---

As the number of fine-tuning experiments grew, I built tooling to run more model trainings in parallel. This repository generates training configurations and SLURM scripts, submits jobs with `sbatch`, separates outputs by run, and helps summarize results.

This work taught me how to manage large experiment sweeps on a compute cluster. I learned how to write SLURM scripts, organize YAML configs, parallelize multiple trainings, manage job outputs, and compare results across runs. It also helped connect machine learning research with the systems work needed to make experiments repeatable.

The repository became part of the broader Foam-GPT workflow because faster experiment management made it easier to test learning rates, model choices, dataset versions, and fine-tuning settings without running everything manually one at a time.

[GitHub repository](https://github.com/ramrow/slurm_job_manager)
