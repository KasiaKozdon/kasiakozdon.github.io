---
title:  "XAI: Explainable AI"
categories: explainableAI
isPost: true
layout: post
---


#XAI: Explainable AI. Introduction.

##What is Explainable AI (XAI)
"Technically, there is no standard and generally accepted definition of explainable AI. Actually, XAI term tends to refer to the movement, initiatives, and efforts made in response to AI transparency and trust concerns, more than to a formal technical concept.” [1].
Since then, we saw a lot of progress, systematisation, and, importantly, criticisms leading to further improvements. Please keep it in mind when reading even relatively recent content.

Why do we care?
Stakeholders:
* End users (e.g. bank loans applicants)
* Decision makers (e.g. doctors)
* Regulatory agencies
* Engineers

Applications:
* Bias detection
* ML troubleshooting
* Assessing model suitability as a product
* Explanation as a product

##Classification of XAI methods
###Complexity-related methods 
* Directly interpretable (e.g. decision trees)
* Reverse engineered (post-hoc)
###Scope-related methods
*Global (how decisions are made in general)
*Local (how a given decision was made)
###Model-related methods
*Model specific (posterior probabilities of nodes in a Bayesian Network)
*Model agnostic: a) visualisation: surrogate model, partial dependence plot; b) knowledge extraction: pedagogical, decompositional; c) influence methods; d) example-based: counterfactuals, criticisms
###Example: saliency maps

##Classification of explanations
We can distinguish the following catergories [2]:
###Application-grounded
which judges explanations based on how much they assist humans in performing a real task; 
###Human-grounded
which judges explanations based on human preference or ability to reason about a model from the explanation;
###Functionally-grounded
which judges explanations without human input, based on some formal proxy for interpretability.

##Prediction interpretation & justification
Limitless explanations can be created. Which explanations are useful? Can the choice of explanation manipulate the user? Based on examples from [3].
###Adding facts (problem solving) preferred over deleting them (logical reasoning)[answer A]
Info on what would make the outcome better preferred to what would make it worse [answer A]
###Perceived fault and causality (how the outcome would be different if the action would have been different) vs perception of blame reduction (how the outcome would be the same if action would have been different)
###Focus on exceptional, controllable, recent, and action-based

##Recommender systems
* Previous choices of the user, e.g. films with favourite actor
* Choices of similar users (collaborative filtering)
* Model features 
* Hybrid 
“(...) previous studies have often evaluated the persuasiveness of the justification and not its justifiability. 
Their experiments showed that for justifiability, feature-based justifications were superior to neighbor-based and user-history-based ones.” [4]


##Counterfactuals
*By definition, cannot be based on data alone (involve scenarios that did not happen)
*Not limited to XAI
**Liability determination, e.g. does smoking cause cancer?
**Strategy assessment, e.g. user was shown advert x , and bought the product. Would the user have bought the product if no advert had been shown?
*Goal-dependent
“﻿An explanation of a decision intended to help the user understand the AI system and make inferences about its future performance could best rely on better-world counterfactuals; 
an explanation intended to ensure the user feels a decision was justified or excusable could rely on worse-world counterfactuals.” 

###Desirable characteristics
*Plausible
*Distributionally faithful
*Possible quality metric: Out of Distribution number 
*Sparse (had few feature differences) 
*Proximate (the closest possible world)
E.g. Nearest Unlike Neighbour
*Preferably actionable

##Summary
*Benefits
*XAI as assistance in ML development

##References
[1] Adadi and Berrada, 2018
[2] Doshi-Velez and Kim, 2017
[3] Byrne, 2019
[4] Biran and Cotton, 2017
