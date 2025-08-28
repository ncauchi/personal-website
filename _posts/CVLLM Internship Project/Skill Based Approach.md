---
title: "Sprint 3: Hierarchical Analysis"
description: Summary
tags:
  - cvllm
date: 2025-07-08
---
<style> .simple-nav a:hover { background-color: #c2956cff !important; color: white !important; } </style> <nav class="simple-nav" style="display: flex; justify-content: space-between; margin: 20px 0; padding: 15px 0; border-top: 2px solid #c2956cff;"> <a href="First Attempt" style="color: #c2956cff; text-decoration: none; font-weight: 600; padding: 8px 16px; border: 2px solid #c2956cff; border-radius: 4px; transition: all 0.3s ease;">← Previous Post</a> <a href="[[Next Note Name]]" style="color: #c2956cff; text-decoration: none; font-weight: 600; padding: 8px 16px; border: 2px solid #c2956cff; border-radius: 4px; transition: all 0.3s ease;">Next Post →</a> </nav>
## Objective

This sprint focused on training a Large Language Model (LLM) to accurately answer questions about cyclic voltammetry (CV) graphs, targeting a comprehensive range of analytical skills. The key innovation was developing a pipeline architecture where fundamental skills like peak identification could support more complex analytical tasks like signal analysis. My goal was to design and implement a complete training pipeline that would enable continuous improvement through error analysis and iterative refinement.

## Background Context

This sprint built upon our team's initial attempt at creating a general CV question-answering system. While that first iteration successfully improved the model's reasoning capabilities, it struggled with applying fundamental electrochemical analysis skills consistently. This gap highlighted the need for a more structured approach to skill development.

> [!tip] Key Learning
> 
> Separating reasoning capabilities from domain-specific skill application proved crucial. A model can understand **what** to do without knowing **how** to execute it properly - these require different training approaches.

What made this sprint particularly valuable was the independence I was given to drive the solution. I designed the strategy, conducted evaluations, and developed the necessary tools while managing a portion of research funds allocated for this initiative. Throughout the process, I collaborated with a senior team member who was working on complementary aspects of the larger project. This experience provided insights into how specialized AI models can bridge the gap between raw data interpretation and expert-level analysis in scientific domains.

_[Figure 1: Comparison of model performance between initial attempt and new pipeline approach would be inserted here]_

## Implementation

The technical implementation centered on a template-based system for generating training data across different analytical skills. The core architecture followed this flow:

**Data Creation Pipeline:**

1. Generate CV graphs through enhanced data augmentation
2. Assign appropriate skill templates based on graph characteristics
3. Apply contextual variations to increase robustness
4. Perform programmatic analysis to determine correct answers
5. Fill templates and format responses for training

_[Figure 2: Data creation flow diagram showing the pipeline from graph generation to formatted training data would be inserted here]_

A crucial design decision was implementing hierarchical skill dependencies, where high-level analytical skills could recursively leverage low-level skills. For example, determining electrochemical reversibility might first call upon peak identification and peak separation measurement functions before making its final assessment.

> [!success] Design Win
> 
> The hierarchical skill architecture mimicked how human experts actually analyze CV graphs - starting with fundamental observations and building up to complex interpretations. This made the model's reasoning more interpretable and debuggable.

I adapted and significantly enhanced our existing graph augmentation tools from the previous sprint, adding new variation mechanisms and features to improve robustness. The development process spanned three weeks, with iterations occurring every 4-5 days. Each iteration incorporated improvements based on systematic performance analysis.

To ensure rigorous evaluation, I implemented confusion matrices for each skill category, providing clear visibility into where the model excelled and where it needed improvement. Additionally, I performed multiple inference runs with temperature variation and used bootstrapping techniques to generate confidence intervals for model performance on test data. This statistical approach provided valuable insights into both average performance and variability across different conditions.

## Challenges & Solutions

**Technical Debt Management** As the system evolved with new skills, modifications, and increasing complexity, technical debt accumulated rapidly. The codebase became increasingly difficult to maintain and extend. While the immediate solution involved planning a comprehensive refactoring (which became the focus of my next sprint), I implemented modular design patterns where possible to minimize further debt accumulation.

> [!warning] Lesson Learned
> 
> Rapid prototyping in research environments creates a tension between "making it work" and "making it maintainable." I learned that even in fast-paced research, investing time in code structure early pays dividends when the system inevitably grows beyond initial scope.

**Question Variation Sensitivity** Initial testing revealed that while the model performed well when questions matched training formats exactly, it was extremely sensitive to slight variations in phrasing. This brittleness would be unacceptable in real-world applications. To address this, I implemented an extensive question variation system, generating multiple phrasings for each skill assessment. This approach successfully made the model more resilient to different question formats while maintaining consistency in its analytical responses.

**Graph Generation Quality** The original graph creation pipeline couldn't generate sufficiently realistic graphs to support complex analytical questions. The graphs were too random and didn't reflect real experimental scenarios. I rebuilt the entire graph generation pipeline to create CV graphs with realistic electrochemical behaviors and experimental conditions, enabling the model to learn from scenarios that would actually appear in laboratory settings.

> [!important] Critical Insight
> 
> Data quality trumps quantity. Spending extra time to generate realistic, physically meaningful training examples improved model performance vastly more than increasing training time on more "samey" augmented data.

## Results/Next Steps

The model achieved strong performance across the skill benchmark suite, with particularly notable improvements in [specific metric placeholder: X%] for fundamental skills and [specific metric placeholder: Y%] for complex analytical tasks. The hierarchical skill architecture proved especially effective, showing [specific metric placeholder: Z%] improvement in multi-step reasoning tasks.

_[Figure 3: Bar graph showing model performance scores across different skill categories would be inserted here]_

The system's evolution exceeded initial expectations in both complexity and capability. This growth required continuous adaptation of development practices and system architecture. The experience underscored the critical importance of clean, readable, and well-structured code in research environments where requirements evolve rapidly.

Looking ahead, the immediate next step involves the refactoring effort to address accumulated technical debt. Following that, we plan to expand the skill set to include more specialized electrochemical techniques and integrate the model into a user-facing interface for beta testing with domain experts.

## What I Learned

• **Analyzing and debugging model training processes** - Developed systematic approaches to identify why models fail on specific tasks and implement targeted solutions

• **Navigating ambiguity in fast-moving research environments** - Made decisive progress despite evolving requirements and uncertain outcomes

• **LLM training and evaluation expertise** - Gained hands-on experience with training, fine-tuning, and evaluating large language models for specialized domains

• **Data mix optimization** - Created and refined complex data generation systems using templates and augmentation techniques

• **Iterative ML system refinement** - Built skills in continuously improving complex systems based on performance metrics and user requirements

• **Cross-disciplinary collaboration** - Successfully bridged electrochemistry and machine learning domains, facilitating communication between research and engineering perspectives

• **Technical debt awareness** - Experienced firsthand how rapid prototyping creates debt and learned strategies for balancing speed with maintainability