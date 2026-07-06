---
layout: post
title: "Learning about progress towards automated AI R&D from CIFAR speedruns"
author: "Rowan Huang & Kaivalya Hariharan"
date: 2026-07-05
category: technical
---

# Learning about progress towards automated AI R&D from CIFAR speedruns

## Introduction

AI agents are improving rapidly at tasks where they're given a clear specification on what to do. However, there's still an open question about how well they're improving on research tasks, where progress comes both from generating good ideas and executing them efficiently. Understanding these capabilities matters because it tells us how much AI agents might accelerate AI development itself.

In this blog post, we give preliminary evidence on AI agent research capabilities by testing their performance on the CIFAR speedrun, which involves training a neural network to 94% accuracy on CIFAR-10 using a single A100 GPU. The goal of this evaluation is to better understand the behavior of models as researchers and explore what factors affect how good models are at research tasks. We ultimately find that both Opus 4.8 and GPT 5.5 are able to make moderate improvements off of the solution they're given.

## Motivation

### Intelligence Explosion

As AI agents get better at doing AI research, they get closer to being able to improve themselves. In particular, if a model can build a better version of itself, and that better version can do the same, progress on AI capabilities will speed up significantly. This loop is often referred to as an intelligence explosion, and in this study we want to get a sense for whether current models are capable of kicking one off.

To understand how close we are to automating AI research in this way, we could theoretically task a current model to train a new model with improved capabilities. But since carrying out such an experiment is prohibitively expensive, we need to look at AI agent research capabilities in a toy setting.

Even in a toy setting, we still want the models to perform the hypothesis generation and experimentation that AI research requires. Further, we want the model to do something optimization flavored, since much of AI research is a search for changes that move a measurable objective through repeated cycles of proposing an idea, running it, and reading the result. For example, we might have it iterate towards a low pretraining loss or a target accuracy threshold with some fixed computational resources.

Tasks like these are often called speedruns, and Karpathy's autoresearch experiments are the canonical example. Understanding how good models are at these kinds of tasks is useful for forecasting whether an intelligence explosion is possible.

### Properties of speedrun tasks

In speedruns, progress can be measured very directly and cheaply, which offers quick feedback loops. A side effect is that progress within a given run can be measured on a curve: compared to tasks where the model spends most of its compute on a single submission per eval, fast iteration gives a trajectory of submissions that forms a curve. We can interpret these as partial progress, which lets us examine the speed of iteration and compare across models.

While progress can be measured directly, there is no clear specification on how to approach the problem. Historically, progress on CIFAR came through adjustments on a multitude of fronts: the current SOTA solution attributes ~5% of its 22% improvement to architecture changes, ~7% to tuning, 5% to vectorized optimization, etc. This lets us see what approaches the models tend towards.

We think these properties are useful given the current state of agent capability. Even if speedruns don't perfectly mimic the distribution of capabilities needed for research, they have properties that set agents up for success, and for that reason the failures we find are more informative.

### Why CIFAR among speedruns

CIFAR has some advantages over other tasks with the above properties, such as the more traditional speedrunning of NanoGPT:

1. It's relatively cheaper to train the model, making it easier for AI agents to iterate and cheaper for us to run the evaluation. Notably, GPU costs, even in this eval, ended up dominating.
2. There's been less effort optimizing CIFAR, which suggests there may be more gains to be made.

Thus, in this blog post, we present results from an evaluation where AI agents are tasked to optimize a CIFAR-10 neural network.

## Methodology

In each eval run, an AI agent modifies a neural network with the goal of reducing training time while maintaining 94% accuracy on CIFAR-10. They start with the solution from Keller Jordan which trains to 94% accuracy in 2.59 seconds on a single NVIDIA A100 GPU. However, due to slight differences in our infrastructure, we got 3.7s @ 0.94 mean accuracy across 50 trials, so this will be the baseline the models work from.

Note that the current state-of-the-art (SOTA) solution is from Hiverge which trains to 94% accuracy in 1.98s. However, we choose to set these two models off at airbench, because we found in previous runs that they were totally incapable of improving over the SOTA solution.

We evaluate two frontier models: Claude Opus 4.8 and GPT 5.5 on xhigh reasoning. They're each evaluated 5 times, and in each evaluation they're given a limit of 100,000,000 tokens. The agent loop is a ReAct agent with bash and python tools. Agents are not given access to the internet.

## Results

Below, we look at Opus 4.8 and GPT 5.5's overall performance and characterize their behaviors as researchers.

### Frontier models were able to advance over the airbench solution in the CIFAR speedrun, through a mixture of hyperparameter tuning and genuinely novel methods

Both GPT 5.5 and Opus 4.8 were able to advance the airbench solution in the CIFAR speedrun, as seen in Figure 1. At the beginning of the runs, Opus 4.8 outperforms GPT 5.5, but by the end of each run, the performance between the two models was very similar.

<img src="/assets/images/fig1_speedrun_tokens.png" width="600">

*Figure 1. Fastest training time with >94% accuracy over tokens spent per model-run. Each thin line corresponds to a model-run, with blue lines corresponding to GPT-5.5 and red lines corresponding to Opus 4.8. Going up along the y-axis denotes better performance, since the y-axis has been flipped. The two thick lines correspond to the means across these model runs. The shaded areas are 95% confidence intervals. The dotted line corresponds to the Hiverge baseline. There were 4 valid runs from Opus 4.8, and 5 valid runs from GPT 5.5.*

### Models have different tendencies as researchers

To better understand the trends in Figure 1, we examine how models acted qualitatively across each eval run.

To start, Figure 2 shows each model's resource use tendencies. We find that Opus 4.8 consistently tried experiments more often than GPT 5.5 did in all of the runs.

<img src="/assets/images/fig3_submissions_tokens.png" width="600">

*Figure 2. Cumulative submission count over tokens spent. Each thin line corresponds to the cumulative submission count per model run, with blue lines corresponding to GPT 5.5 and red lines corresponding to Opus 4.8. The two thick lines correspond to the means across these model runs. The shaded areas are 95% confidence intervals. There were 4 valid runs from Opus 4.8, and 5 valid runs from GPT 5.5.*

Next, Figure 3 shows what ideas models tried in each run and Figure 4 shows which ideas were successful in improving model performance across each run. We find that the models performed a similar number of unique techniques, which is interesting given that Opus 4.8 tried more experiments. Both models spent much of their time on hyperparameter tuning and infrastructure.

More interestingly, we find that the distribution of techniques that were in best-so-far submissions were often different from the distribution of techniques tried across the entire run. This is the most stark for Opus 4.8, which only had success in adjusting the training schedule and hyper parameters. GPT 5.5, on the other hand, had success in a wider variety of techniques. In combination with Figure 1, this suggests that Opus 4.8 generally found the hyperparameter "solution" early on in the run, and spent the rest of the run trying and failing to find alternative solutions. GPT 5.5 instead was able to find a wider variety of successful techniques and slowly iterated towards a better solution across the model runs. At the end, however, both models converged to a similar performance.

Notably, Opus 4.8 proposed a downsampling method that is a genuine novelty, even with respect to the Hiverge SOTA solution. However, it did not consistently bring up this idea in each run, and also did not successfully execute the idea each time it was proposed.

<img src="/assets/images/fig_strategies_allchanges_reclassified.png" width="600">

*Figure 3. Model strategies per run across all submissions. Each bar corresponds to a model run, with height showing the number of unique techniques the agent added or modified during that run. Colors correspond to idea categories to give a qualitative sense of the kind of ideas models attempted in their code edits, as classified by an independent instance of Opus 4.8. Techniques inherited unchanged from the airbench baseline are not counted.*

<img src="/assets/images/fig_strategies_bestsofar.png" width="600">

*Figure 4. Model strategies per run for the best-so-far submission. Each bar corresponds to a model run, with height showing the number of unique techniques present in the best-performing submissions across the model run. Colors correspond to idea categories. Techniques inherited unchanged from the airbench baseline are not counted.*

## Conclusion

Both Opus 4.8 and GPT 5.5 improved on the airbench CIFAR speedrun solution, which is some evidence that current agents can make real research progress when the task is set up in their favor. However, as noted in the methodology section, they were unable to improve upon the actual SOTA solution from Hiverge. Further, their improvements in this evaluation were often marginal adjustments to the given baseline, rather than through genuinely novel ideas.

Since an intelligence explosion depends on whether models can generate and execute good ideas on their own, these results suggest that ability is still uneven for now.

## Appendix: Lessons on Eval Dev

This particular methodology was informed by a few failed evaluation runs. Here are some lessons we've learned in the process of conducting this evaluation.

- **Models are highly sensitive to the choice of baseline neural network implementation, i.e., the script that gives a starting-point score for the models to improve upon.** In general, agent performance on the task scales somewhat consistently with the performance of the initial baseline. That is, agents tend to improve marginally off of what they were given initially, instead of trying to work their hardest on a given task.
- **Contamination can complicate cross-model comparisons.** One intuitive way to run this evaluation is to start the agents off at a very easy baseline (i.e., a vanilla ResNet) and see how much they improve. However, we found that, even putting aside challenges with baseline sensitivity, each model had memorized different historical solutions. Our ultimate resolution is giving agents SOTA for the initial attempts, and stepping down the baseline depending on their initial performance to scale the difficulty of the eval. In this iteration, we report results where Opus 4.8 and GPT 5.5 started at the airbench solution, since they were unable to improve over the current SOTA Hiverge solution.
- **If given a "bad" baseline, the agent will spend very significant amounts of time trying to fix the baseline.** In earlier runs, we started the agents on a baseline that was calibrated to hit 94% accuracy almost exactly, but since there's some variance in the accuracy per training run, the model's first submission of the baseline code might've been under 94%. This sent the models on a loop of trying to fix the baseline, instead of working on trying new things.
- **Elicitation matters for model performance.** Models tried much harder (and reward hacked more) when they were told in the prompt that it was possible to improve upon the SOTA solution.
