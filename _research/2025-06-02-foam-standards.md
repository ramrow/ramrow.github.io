---
title: "Foam Standards: LLM Deployment and Evaluation"
category: research_projects
permalink: /research/foam-standards/
excerpt: >
  This repository expanded the research from fine-tuning into deployment and evaluation. I learned how to run fine-tuned and baseline models through Ollama and vLLM, evaluate generated OpenFOAM case files, compare model outputs, and summarize performance inside a Foam-Agent workflow.
date: 2025-06-02
venue: 'Summer 2025-Present Undergraduate Research, Rensselaer Polytechnic Institute'
link: 'https://github.com/ramrow/foam_standards'
---

This repository focuses on evaluating Foam-Agent and Foam-GPT style workflows with both fine-tuned and baseline LLMs. After the first round of fine-tuning, this work helped move the project from "the model trains" to "the model can be deployed, called, and judged inside a realistic OpenFOAM automation pipeline."

Through this work, I learned how to deploy models locally and on servers with Ollama and vLLM. I also worked with evaluation scripts that compare generated OpenFOAM case files, track pass and fail outcomes, and summarize whether model outputs are useful for CFD simulation setup.

This stage was important because fine-tuning alone does not prove a model is useful. The model has to produce files that match OpenFOAM expectations, work inside the surrounding agent workflow, and generate outputs that can be evaluated against simulation-oriented checks.

[GitHub repository](https://github.com/ramrow/foam_standards)
