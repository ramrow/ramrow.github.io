---
title: "Controlled Dataset Branching"
category: research_projects
permalink: /research/controlled-dataset-branching/
excerpt: >
  This repository improved the training data through controlled OpenFOAM case branching. I generated traceable case variants from validated base cases, adjusted physical parameters such as velocity, reran validation, and accepted only dataset rows that passed the workflow.
date: 2025-06-04
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/controlled_dataset_branching'
---

This repository explores controlled dataset expansion for OpenFOAM fine-tuning. The goal was to improve the dataset without creating untraceable or low-quality examples.

The pipeline starts from validated OpenFOAM case folders and creates controlled variants, such as velocity changes of +10%, +20%, and +30%. Instead of generating arbitrary new examples, the process modifies known working cases, patches the relevant OpenFOAM files, reruns validation, and saves accepted dataset rows only when the generated case passes the required checks.

This helped me learn how data quality affects fine-tuned model behavior. For engineering-focused LLMs, dataset augmentation has to preserve physical meaning, file structure, and simulation validity. This repository was one step toward making the training data broader while keeping it controlled and inspectable.

[GitHub repository](https://github.com/ramrow/controlled_dataset_branching)
