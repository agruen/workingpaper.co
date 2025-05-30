---
title: Concept Note - A Data Access Strategy
date: 2025-05-29 15:29:52 Z
description: What are all the parts of a complete data access framework?
featured_image: "/images/gradients/yellow-green.png"
---

_This was a note I prepared about a year ago on conceptualizing data access in general.  I'm publishing here as I think the framework could be useful to those working in the field.  Feedback is, of course, [incredibly welcome](https://workingpaper.co/contact)._

_Andrew_

## Concept Note: A Data Access Strategy
### What are all the parts of a complete data access framework?

If we take as a given that evidence-based policymaking is preferable to other forms, and we want to create technology that conforms to our normative view of what a good, verdant, democratic world looks like, there is precisely one piece of advocacy we need: data access.  We need access to the data that would help us to make informed decisions about the world in which we live, a world that is today almost entirely mediated by technology.  However, unlike the analog world, where artifacts could be (laboriously) turned into data without any permission or special access (e.g. researchers could count the number of references to a topic on national news broadcasts), our technology-mediated world operates differently.  Today, the artifacts are held by the (overwhelmingly private) organizations that build our technology, and so we need a different mechanism to access them.

If we also believe that data access is not an end in itself, but instead the first step in a scientific process that endeavors to develop theories that predict outcomes in the real world, we should design our data access advocacy in support of that science.  And we should think clearly about prioritization, not just about access.

If, finally, we were serious about changing the status quo, where most of this data is inaccessible – where there are significant information asymmetries between private and public actors – we would outline both what a good outcome looks like, along with every lever we’d need to press in order to get there.

This note outlines how we’d do that.

### What Good Looks Like

#### Supporting the Full Scope of Scientific Inquiry

At the highest possible level, there are two types of scientific inquiry relevant to policy making: observational and experimental.  Observational research can help us understand what is happening in the world today.  Experimental research can help us understand why.

If we aim to get the data held within the aforementioned organizations, there are three different mechanisms: data can be (1) taken from them, (2) given by them to researchers, or (3) generated by them for researchers.  

### Data Access Mechanisms

Put more politely, the mechanisms available are: 

1. Donations and Scraping (individual level, may or may not be consented data sharing) – users give their own data to researchers through various mechanisms, or researchers directly collect it  
2. Observational log data (group level, non-consented data sharing) – companies collect observational data about what people do when interacting with their systems and give that data to researchers to analyze  
3. Experimental access (individual or group level, consented experimental treatments) - companies enable users to consent to entirely different experiences with their products, designed by independent, external researchers

As referenced above, there are four criteria worth considering for each data access mechanism:

1. Consent - do the people represented in the data give researchers unencumbered, affirmative, and informed consent to use it for a specified purpose.  
2. Collection Source - how the data arrives at the scientific collection instrument  
3. Individual/Aggregate - do the data represent an individual or an aggregation of people  
4. Causal Inference - can the data be used to infer causality of some kind

**A Framework for Data Access**

|  | Donations and Scraping | Observational Log Data | Experimental Access |
| :---- | ----- | ----- | ----- |
| **Consent** | Not Necessarily | Not Necessarily | Yes |
| **Collection Source** | Organization → Researcher<br />User → Researcher<br />Web → Researcher  | Organization → Researcher | Organization → Researcher |
| **Individual/ Aggregate** | Individual | Both | Both |
| **Causal Inference** | No | No | Yes |

Combining these into the above table helps to understand why all the different methods are required.  For example, if researchers wish to understand an important but illegal social phenomenon (geographic boundaries of the opioid epidemic), they cannot rely on consent; criminals are unlikely to consent to sharing incriminating evidence.  Similarly, if a researcher wishes to understand a nationally- representative population (which may NOT be a representative population of a given technology’s users), they are best placed to recruit a sample themselves and ask them directly for donations.  Finally, if researchers seek to understand the impact of a specific technology on wider outcomes (feed ranking algorithms on knowledge retention), they will need to systematically control and vary that technology.

### Theories of Change

Two paths to data access exist: those where entities voluntarily make the data they hold available, and those where they are forced to do so.  Understanding both is necessary in order to maximize the opportunities for data to reach researchers.  This note argues that, just like a strategy should be developed for researchers to use all three data access mechanism, we should also aim to use both access schemes.

#### Voluntary

The vast majority of data access for research to date has been under voluntary regimes.  There were periods of remarkable openness, where large data-collecting organizations shared relatively freely.  With both poor behavior on the part of a small group of researchers and public backlash (Cambridge Analytica), alongside the bringing into force of stronger privacy regulation (GDPR, FTC Consent Decrees, etc.), this access was dramatically curtailed. 

Broadly speaking, where voluntary data access remains is in domains where the rules, norms and law around said data sharing are clearly understood; where the penalties for mistakes are low; and where the organizations that hold the data are benefited by sharing it (most often plaudits; very, very rarely payment).  When data is shared voluntarily, it is also often, but not always, not broadly available.  Instead, access reverts to trust networks, which are often inherently inequitable.

##### Paid

While researchers rarely have the resources to pay the amounts that various companies would charge (e.g. an amount that was economically incentivizing), it is worth noting here because, even now it remains an option for various forms of research.  For example, some companies offer access to vast swaths of user data (mostly in the form of either public content or observational logs) for pay. Typical customers are marketers and other for-profit entities like LLM developers.

#### Mandatory

Relatively recently, data access has been included in pieces of proposed or passed legislation.  The strongest form of legal mandate that has become law to date, Article 40 of the EU’s Digital Services Act, has yet to come into full force, but from it we have already learned an important lesson: be careful what you wish for.

As various Very Large Online Platforms (VLOPs) — the companies subject to the Digital Services Act's [data sharing provisions](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32022R2065#art_40) — have prepared to come into compliance with the law, they have trended toward minimal and literal interpretations of their obligations.  While this is an entirely rational approach to new regulation that carries both significant business risk (reputational and otherwise), along with very large financial risk (in the form of fines), it has had a perverse effect on data access.  For example, some VLOPs have produced the required “real time” access to “public content” in ways that are so onerous to use that they have, effectively, reduced the amount of useful data shared, all while truthfully claiming they are sharing more than ever before.

While the ultimate implementation of Article 40 has yet to play out, the lesson learned here in early 2024 is that mandatory data access has to either be immensely prescriptive in what organizations must do to share, or must build-in the ability for an independent, fair arbiter to create new specifics as the world changes.
