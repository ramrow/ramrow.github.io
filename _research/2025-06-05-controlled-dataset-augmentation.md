---
title: "Controlled Dataset Augmentation with Claude"
category: research_projects
permalink: /research/controlled-dataset-augmentation/
excerpt: >
  This repository extends the dataset work with controlled augmentation. It uses parameter perturbations and Claude-assisted data generation while keeping outputs constrained by validation, so augmented OpenFOAM examples are accepted only when they remain usable.
date: 2025-06-05
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/controlled_dataset_augmentation'
---

This repository expands the dataset improvement work into a more complete controlled augmentation pipeline. The goal was to create more diverse OpenFOAM training examples while avoiding the common problem of generated data that looks plausible but fails when used.

The pipeline creates controlled numeric perturbations for parameters such as velocity, viscosity, and density. It then runs generated variants through the Foam-Agent validation workflow and only accepts examples that pass. This keeps the dataset tied to usable simulation cases rather than unverified text.

I also used Claude through AWS Bedrock for data augmentation and case-generation support. The important part of the workflow is that Claude-assisted augmentation was not treated as automatically correct; outputs still had to pass validation before becoming part of the dataset.

[GitHub repository](https://github.com/ramrow/controlled_dataset_augmentation)
