---
title: "Foam-GPT Failure Analysis"
category: research_projects
permalink: /research/failure-analysis/
excerpt: >
  This repository studies why the fine-tuned model was not yet reliable enough for OpenFOAM automation. I analyzed failed generations, compared expected and generated files, reviewed syntax and structure problems, and connected model errors to practical engineering usefulness.
date: 2025-06-03
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/failure_analysis'
---

This repository focuses on understanding why the fine-tuned Foam-GPT models were still not good enough for reliable OpenFOAM automation. Instead of only looking at aggregate metrics, I examined the actual generated files and failure cases.

The analysis included comparing model outputs against expected OpenFOAM files, checking pass and fail results, reviewing file-level differences, and identifying recurring failure modes. These included missing required files, invalid syntax, plausible but incorrect values, and outputs that did not preserve the structure expected by Foam-Agent or OpenFOAM.

This work helped connect model behavior to engineering usefulness. A model can appear promising from training loss or general benchmarks, but for this project the real question is whether it can generate complete, valid, simulation-ready OpenFOAM cases.

[GitHub repository](https://github.com/ramrow/failure_analysis)
