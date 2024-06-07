layout: post
title: "Welcome to my new site!"
date: 2023-07-17
categories: to-remove

# Counterfactuals
* By definition, cannot be based on data alone (involve scenarios that did not happen)
* Not limited to XAI
  * Liability determination, e.g. does smoking cause cancer?
  * Strategy assessment, e.g. user was shown advert x , and bought the product. Would the user have bought the product if no advert had been shown?
* Goal-dependent
“﻿An explanation of a decision intended to help the user understand the AI system and make inferences about its future performance could best rely on better-world counterfactuals; 
an explanation intended to ensure the user feels a decision was justified or excusable could rely on worse-world counterfactuals.” 

## Desirable characteristics
* Plausible
* Distributionally faithful
* Possible quality metric: Out of Distribution number 
* Sparse (had few feature differences) 
* Proximate (the closest possible world)
E.g. Nearest Unlike Neighbour
* Preferably actionable

# Prediction interpretation & justification
Limitless explanations can be created. Which explanations are useful? Can the choice of explanation manipulate the user? Based on examples from [3].
### Adding facts (problem solving) preferred over deleting them (logical reasoning)[answer A]
Info on what would make the outcome better preferred to what would make it worse [answer A]
### Perceived fault and causality (how the outcome would be different if the action would have been different) vs perception of blame reduction (how the outcome would be the same if action would have been different)
### Focus on exceptional, controllable, recent, and action-based
