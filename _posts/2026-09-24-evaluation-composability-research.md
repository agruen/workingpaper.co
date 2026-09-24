---
title: The Research That Can Answer Questions About AI Evaluation Composability
subtitle: "“Benchmarks Aren’t Composable” is an important mantra for AI deployers - we know this through observation. However, before anyone can say conclusively whether an evaluation result survives fine-tuning, we need to know how much of an evaluation result is noise. Here are two project concepts that would help us answer “Is evaluation X on fine-tuned model Y composable?”."
author: Bennett Hillenbrand
author_url: /bennett-hillenbrand
date: 2026-09-24 17:00:00 -0400
description: Before anyone can say whether an evaluation result survives fine-tuning, we need to know how much of that result is noise. Two research projects that would move the composability question forward.
featured_image: "/images/blog/evaluation-composability.jpg"
photo_credit: 'Photo: <a href="https://commons.wikimedia.org/wiki/File:Seismogram_at_Weston_Observatory.JPG">Seismogram at Weston Observatory</a> by Z22, via Wikimedia Commons, <a href="https://creativecommons.org/licenses/by-sa/3.0/">CC BY-SA 3.0</a>'
---

In a recent conversation about whether AI evaluations are composable, I was asked a fair question: “what research projects would actually move this question forward?” This post is my attempt at answering that question.

## Where we are right now

There are three things we currently know that point us in the direction of what we need to answer next.

**Safety benchmarking results shift unpredictably after fine-tuning.** CDT's AI Governance Lab, working with MIT's Algorithmic Alignment Group, [compared publicly available medical and legal fine-tunes against their base models](https://cdt.org/insights/out-of-tune-fine-tuning-foundation-models-leads-to-unpredictable-safety-drift/). Some of these fine-tuned models came out safer according to the benchmarks used and some came out less safe compared to their base models. The authors highlighted that no particular fine-tuning choice explained which way a model would go. They also noted that how much a model was modified didn't seem to have prediction power for how much its safety changed either. Their reasonable conclusion, then, is that nobody should assume a fine-tuned model inherits the safety properties of its base.

Reading that work, I kept returning to an implicit question that the authors brought up as a likely confound. How much of the observed drift comes from the fine-tuning, and how much comes from the safety evaluator used in the evaluation? If the measurement moves around on its own, some of what might look like fine-tuning drift is simply noise from the evaluation.

**Almost no one reports measurement error in their AI benchmarks.** Solomon Messing's [recent paper on hidden measurement error in LLM pipelines](https://arxiv.org/abs/2604.11581) surveys thirteen widely used benchmarks and annotation studies, and while four reported confidence intervals, those CIs captured only the variance associated with test item sampling. Relatedly, earlier this year, NIST used GLMMs [to examine benchmark variance attributable to component question difficulty](https://www.nist.gov/news-events/news/2026/02/new-report-expanding-ai-evaluation-toolbox-statistical-models). None of the thirteen benchmarks or studies separated out the variance that comes from the choice of judge model, prompt wording, or temperature. Naive standard errors come out 40 to 60 percent smaller than they should, per Messing’s work. That gap gets worse as you add items, because judge and prompt variance doesn't shrink with sample size. In 2024, Anthropic published [a statistical approach to putting error bars on evals](https://arxiv.org/abs/2411.00640), which was a positive step, but it is guidance for a lab running its own evaluations and there isn’t evidence that the approach has been adapted and adopted by public benchmark developers. (Disclosure: Working Paper’s Principals, Andrew Gruen and Bennett Hillenbrand, are included in the acknowledgements of Messing’s paper.)

**Measurement error can be used to game, or “hack”, benchmarks.** Messing draws on [documented cases via “The Leaderboard Illusion” work of Singh et al.](https://arxiv.org/abs/2504.20879) of developers testing many private model variants on a public leaderboard and publishing only the best one. On Chatbot Arena, he estimates that picking the best result sourced from 27 benchmark runs nets about 45 Elo points from sampling alone. That is enough to swap the order of adjacent models in a leaderboard. This moves unreported variance from an academic measurement problem space into an integrity problem space.

MLCommons, an organization Working Paper supports, is about to release a safety benchmark with margins of error that account for the full evaluation pipeline. As far as we know, no other widely used benchmark does this yet.

## Given where we are, what research moves the ball?

**Generating margins of error for the benchmarks people already use.** For select high-use benchmarks, a reasonable project to take on would be to report how wide the interval is around published scores for that benchmark, and how many of the point estimates from a leaderboard's rankings sit within a noise threshold.

**Why this project?** Messing's Total Evaluation Error framework makes it possible to estimate a margin of error. A small pilot can generate variance components under stated assumptions. The work shows that sampling across model providers and model sizes, and across the judge, prompt, and temperature choices for each benchmark often provides a far more reasonable estimate of 95% coverage than alternative approaches.

This could create a stir. Leaderboards are more frequently being used as decision inputs. Procurement teams, investors, and policymakers read them as pure rank orders. If the ordering on a popular leaderboard is mostly noise, the ecosystem needs to know, and benchmark developers need a path to address this.

**Answering questions about composability.** Once margins of error estimates are in place, a set of interesting and useful questions opens up that we can't answer today. When a deployer fine-tunes a model, adds RAG to a deployment, or changes the system prompt, does the downstream model inherit the upstream evaluation result, or at least stay correlated with it? Under which (set of) actions (and at what magnitude of change) does that hold, and can it be predicted in advance?

**Why this project?** Right now we have to take a blanket position that evaluations aren't composable. We hold that position because we have seen it be true in many cases, including the CDT results. That position currently rests on observation, and with uncertainty measurement in place it can be tested. It may, in fact, turn out to be falsifiable in useful ways.

For example, one of the more useful outcomes for the AI ecosystem of such a study is that the result would be deterministic. E.g. a class of modification with given properties would reliably preserve (or break) a given evaluation result. That would give deployers a better option than "retest everything all the time." It would also give policymakers a better trigger for downstream obligations than “how much” a model was modified.

Notably, this second project has a hard dependency on the margins of error project. Without error bars, we wouldn’t be able to tell drift from noise, so any potential understanding of composability from this second project would be confounded.

## Why we care about this

Working Paper's focus sits at the interaction point of where product decisions turn out to be policy decisions. To us, this is clearly one of those such problems. Frameworks like the EU AI Act assign downstream obligations partly by how much a model was modified, and the apparent lack of determinism in the fine-tuning changes described in CDT’s work seems to suggest that obligation is driven by a weak proxy. A better proxy likely exists, but figuring out what that proxy is requires measurement - which we can’t reliably do without understanding how precise our evaluation measurements are in the first place.

If you're working on either of these problems, or want to fund or host the work, [get in touch](/contact).
