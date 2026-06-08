---
title: Responsible Disclosure in AI Benchmarking
subtitle: We saw the responsible disclosure problem coming for AI. Here's how we helped a client get ahead of it.
date: 2026-06-08 12:30:00 Z
description: Working Paper recognized the policy implications of a product launch early, and then to moved on both the build and the broader norm at the same time.  We ended up setting international standards.
featured_image: "/images/gradients/magenta-purple.png"
---

Working Paper supports clients on technical product decisions that are policy decisions in disguise. The challenge of responsible disclosure in AI evaluation is a clean example of exactly that, and it's worth walking through how we found it and what we did with our client, MLCommons.

## What we found

The security world has run on coordinated vulnerability disclosure for decades. A researcher finds a flaw, tells the vendor privately, the vendor patches it, deployers ship updates, and the details go public only after a fix is in place. It's a good system. It also rests entirely on one assumption: the affected system can be fixed and fixing it ends the hazard.

While advising MLCommons on its security benchmark program, we ran the Working Paper standard product responsibility review and ran squarely into the fact that this assumption simply doesn't hold for AI evaluation - especially when it comes to open weight models.  We saw that the field was quietly importin this standard disclosure model that wasn’t fit for purpose. Three properties drive that mismatch:

- **Evaluation findings are dual-use.** A result that tells defenders how a system behaves tells adversaries the same thing. The danger isn't usually a leaked secret capability; it's that the finding lowers the cost of locating one. The right unit of analysis is uplift: the reduction in effort, time, expertise, or resources an actor needs. An open question we are now working through is, “Which categories of benchmark results are never acceptable to publish because they enable dangerous uplift potential.”
- **Feedback to the developer can corrupt the test.** The reliability benchmarks we work on with MLCommons are meant to provide cross-industry, comparable results via a standardized evaluation. Any benchmark meant to run more than once has to give developers enough to improve the underlying property without giving them enough to overfit their models to the specific test items. This creates a balancing act - one has to disclose enough that the developers can act on it, but not so much that they learn how to game the test. Get that boundary wrong and benchmarking scores will improve on paper, without improving the reliability of the system.
- **You can't patch an open-weight model in practice.** Open-weight systems break the old responsible disclosure model. A new version of an open weight model is a new artifact, not an update. Old copies of open weight models are still in use, unmodified, and in the wild indefinitely. Defenders would need to take down the open weights and then remediate every individual deployment - which will simply never happen. These deployed open weight systems with identified hazards then represent information hazards, not cybersecurity ones, and thus disclosure for those systems has to be handled in a different way.

None of these is exotic on its own. The insight was seeing that together they invalidate the inherited paradigm, and that an evaluation operator who didn't address them up front would be building a credibility risk straight into its flagship work.

## What we did about it

Spotting a structural problem is only useful if it changes what gets built. So we worked with MLCommons on two fronts at once.

First, into the product. We helped ensure that this responsible-disclosure thinking was designed into the jailbreak benchmark from the start rather than bolted on after launch including: version-pinned findings, disciplined granularity in the most sensitive categories, and a clear line between what's actionable for a developer and what would enable gaming the test.

Second, into the standard. A disclosure norm is only as strong as the consensus behind it, so the durable fix lives in a standards body, not in any single operator's house rules. Our team holds national-body, liaison, and drafting roles in ISO/IEC JTC 1/SC 42, and we helped carry these principles into the work now feeding ISO/IEC TS 42119-8. The result is that MLCommons can launch a benchmark whose disclosure policy is aligned, in advance, with the international standard taking shape — rather than waiting to retrofit it later.

## Why this is the work we do

This is the pattern we look for on every engagement. The disclosure question -- and those like it -- never arrives labeled as a policy problem. It shows up as a product decision about what a benchmark publishes and when. Our job is to recognize, early, when one of those decisions has governance consequences that will outlive the launch, and then to move on both the build and the broader norm at the same time, so a client isn't left defending a one-off choice against a standard that lands a year later.

MLCommons is doing the hard part: building the benchmark and putting its name behind a public commitment. We're glad to have helped them see around this corner before they reached it.