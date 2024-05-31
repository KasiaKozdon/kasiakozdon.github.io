---
title:  "XAI: Explainable AI. An introduction."
categories: [explainableAI, 101]
isPost: true
layout: post
---


# XAI: Explainable AI. An introduction.
With the rapidly increasing abundance of AI in all areas of our lives, we are starting to pay more attention to how exactly its decisions are produced. Methodologies assisting with gaining understanding of the AI models are referred to as Explainable AI (XAI).
We will talk in more detail about what XAI is and why it matters; about how the explanations can be useful, but also misleading.

## What is Explainable AI (XAI)
Lets start by clarifying what we mean by XAI. According to IBM:
>"Explainable artificial intelligence (XAI) is a set of processes and methods that allows human users to comprehend and trust the results and output created by machine learning algorithms. Explainable AI is used to describe an AI model, its expected impact and potential biases. It helps characterize model accuracy, fairness, transparency and outcomes in AI-powered decision making." [0]

That's a lot of words, but little concrete details. The reason for this vagueness is that:
>"Technically, there is no standard and generally accepted definition of explainable AI. Actually, XAI term tends to refer to the movement, initiatives, and efforts made in response to AI transparency and trust concerns, more than to a formal technical concept.” [1]

There is no black and white rule defining what is and what is not XAI. Still, during the last few years, we saw a lot of progress, systematisation, and, importantly, criticisms leading to further improvements. According to Google trends, XAI is an increasingly popular term.

![XAI google trends](https://github.com/KasiaKozdon/kasiakozdon.github.io/blob/XAI/_assets/2024-05-09-XAI-Explainable-AI/XAI_google_trends.png)

Because it is important to understand things in proportion (aka Hans Rosling's [rule nr 5](https://www.gapminder.org/factfulness/size/)), lets compare that trendline to the AI trend (in red):
![XAI vs AI google trends](https://github.com/KasiaKozdon/kasiakozdon.github.io/blob/XAI/_assets/2024-05-09-XAI-Explainable-AI/XAI_vs_AI_google_trends.png)
Popularity of XAI may be increasing, but it remains a niche subject in comparison to the popularity of AI in general. XAI is sometimes seen as being at odds with making the models better, as a distraction from the "main" objective and a resourses sink. This article is intended to clarify this misconception, and highlight the benefits and XAI for general public, engineers, and businesses.

## Who can benefit from XAI?
When it comes to AI, all of us are stakeholders, mostly in more than one way. Use of XAI can benefit all stakeholder groups.  
**Users** and **by-standers** (non-users who may still be affected). In some cases, the user has the right to explanation.   
**Decision makers**, non-AI experts who use AI to augment their decisions. This includes doctors.    
**Regulatory agencies**... well, lets hope that when they benefit, it is for our own benefit. 
**ML engineers** are rarely listed as a group benefitting from XAI; they are usually seen as being forced to implement XAI for the benefit of other stakeholders. However, engineers are already routinely using XAI techniques, even if not under this name. Techniques used to gain understanding of the model's strengths and weaknesses easily fall under the XAI umbrella. Their use changes model development from a blind hyperparameters grid search to a data-driven decision process. Other benefits of XAI include understanding what in the data and model matters in order to scale down the less needed parts. This benefits the efforts to drastically scale down the amount of resources needed for LLMs; similarly, it benefits the miniaturisation efforts are taking place at the TinyML end of ML spectrum.   
**Business decision-makers** can take advantage of XAI to get information on model's suitability as a product. This can include e.g. assessing whether the model performs well on the markets of interest; under what conditions the model is likely to fail. Finally, explanation itself can be a product or a differentiator of a product! We will look at this case later, illustrated by recommender systems.

## Classification of XAI methods
It's time to introduce a bit more systematisation. I will use XAI classification proposed by [Adadi and Berrada](https://ieeexplore.ieee.org/document/8466590). The categories are not exclusive; a model can be assessed within each of the categories.
### Complexity-related methods 
Here, we can talk about methods that are **directly interpretable**, or that can be **reverse engineered** (post-hoc). This is sometimes presented as Interpretable AI vs Explainable AI.  
Directly interpretable models, as the name suggests, can be understood readily, with no additional methodology required. Examples include decision trees. A decision tree is a hierarchical model where the branching points (nodes) are inquiries, and branches represent possible answer. Traversing the tree culminates in reaching an end node representing a decision. Such trees used to be constructed manually; now are a common trained ML model.   
![decision tree](https://github.com/KasiaKozdon/kasiakozdon.github.io/blob/XAI/_assets/2024-05-09-XAI-Explainable-AI/decision_tree.png)  
Reverse engineered methods apply to models which are black boxes. The models are developed, and only then, post hoc, explainability methodologies are applied. 

### Scope-related methods
Explanations can also be provided to capture how model's decisions are made in general - these are referred to as **global** , or to explain how a given decision was made (**local**). 
### Model-related methods
Some of the XAI methods are **model specific**, they work based on unique features of a given model type. An example includes explanations based on posterior probabilities of nodes in a Bayesian Network. While these XAI methods lack generalisability, they make up for it with excelling at making the most out of the model characteristics.   
**Model agnostic** methods can be applied to a wide range of ML models. These include visualisations, knowledge extraction, influence methods, and example-based methods. To start with, we have **visualisations**, e.g. created with surrogate models and partial dependence plots. Surrogate models are simpler, more easily interpretable or explainable models trained on the pairs input-output of the model under investigation (which was trained on pairs input-correct answer). Development of surrogate models presents a bit of cat and mouse problem. A simple surrogate model fulfills the requirement for interpretability; but due to its simplicity, it may fail to faithfully capture the behaviour of the model under investigation. A more complex surrogate model could do a better job at capturing the dynamics of the investigated model - but would it still provide the benefit of interpretability or explainability? This dillema illustrates that XAI techniques can shift the problem instead of solving it. Their correctness requires maybe even more scrutiny than the original model, given the trustworthiness they are assumed to provide.  
Partial dependence plots are an example of a quite different visualisation. They illustrate a relation between an input feature or features and the output of the model. Usually, all but one features are kept constant, while the feature of interest is varied and the resulting output captured. Through this, we can see whether the impact of the feature is linear, monotonic etc.  
We could also try to **extract the "knowledge"** from the model. This could rely on extracting the rules, in effect creating a system resembling Good Old Fashioned AI, a rule-based expert system. Alternatively, we could destill the model, compress it by using the original model as a teacher for a smaller, transparent model. Here, we would typically use not only the class predicted by the teacher model, but the predicted probabilities (logits, to be specific) of all possible classes, thus also providing information about the relations between the classess to the student network.  
Conversely, **influence methods** estimate the relevance of a feature by altering either the input or internal parameters of the model, then measuring the impact of these alterations on the model's dynamics, predictions and errors.   
Finally, we have **example-based** explanations. Here, we can use *prototypes* to demonstrate representative data examples, and *criticisms* to demonstrate underrepresented samples the model may not generalise to. There are also *counterfactuals*, which resemble adversarial examples (data samples with alterations which change the predictions), but designed with focus to improve understanding of the model. More about these later.    

### Example: saliency maps
Lets illustrate how an explanation can fit into the above categories using saliency maps. This method is model specific, it is applied to image inputs of CNNs. Multiple types of saliency maps exist, but they share visualisation of which pixels contributed to the prediction the most. The method is local, it illustrates how a decision on one particular image was made.
![saliency maps](https://github.com/KasiaKozdon/kasiakozdon.github.io/blob/XAI/_assets/2024-05-09-XAI-Explainable-AI/smoothgrad.png)  
It is very likely that even if you do not work with CNNs, you came across these. They offer intuitive, easily interpretable information that frequently made its way to popular science articles. The image above is aligned with our gut feeling for how a gold fish or a bear could be recognised; what features could be relied on. And here I would like to strongly point something out: I never told you if the network how well the network was doing, whether it classified every eye as a fish and every dog muzzle as a bear. Likely, seeing an explanation that matched your intuitive sense of what is correct gave you trust in the method and in the model. Visualisations of explanations (have been reported)[https://harmanpk.github.io/Papers/CHI2020_Interpretability.pdf] to elicit trust even in expert users, and even in the absence of the understanding of the underlaying mechansms and ability to assess the explanation's correctness: "[The tool] shows visualizations of ML models, which is not something anything else I have worked with has done. It’s very transparent, and that makes me trust it more".  

## Evaluation of explanations
Explanations themselves can assessed, e.g. based on for whom and in what context they are intended to serve. [Doshi-Velez and Kim](https://arxiv.org/pdf/1702.08608) proposed distinguish three categories of explanation evaluations: application-grounded, human-grounded, and functionally-grounded.    
**Application-grounded** explanation evaluations assess how the explanations assist humans in performing a real task. Their success can be assessed by the performance improvement of the person, and therefore indirectly. Studies with medical [doctors](https://youtu.be/htjpbbvHJQo?si=hjkI0HNWiY6760_n) shown that providing access to both model predictions and their explanation resulted in the highest diagnosis accuracy. Interestingly, providing explanations that were incorrect or low quality had a negative impact, suggesting that it was the correctness of the provided explanation rather than a psychological effect of the availability of any explanation that mattered for the performance.    

**Human-grounded** explanation assessments are based on human preference or ability to reason about a model from the explanation. Capturing preferences can be as simple as asking users to select their preferred explanation. To assess the ability of the explanation to improve person's ability to reason about the model, we can present a scenario alongside the model's explanation, prompting individuals to predict the model's output. The correctness of their prediction is related to the quality of the explanation.  
**Functionally-grounded** which judges explanations without human input, based on some formal proxy for interpretability. The proxies could be e.g. the number of rules required to explain the system or alignment of the interpretable surrogate model with the black box model. The formality and quantitativeness of this approach may create the impression that the explanations were conformed to be correct. In reality, the quentitative metrics can be unrelated to the correctness of the explanation. Similarly, the use of metrics can create the impression of objectiveness; however, the choice and design of the metrics can be rooted in subjective human choices. Overall, you should evaluate functionally-grounded explanations with the same level of scrutiny as you would with others. 
Explanation evaluations can produce inconsistent results. Whenever  human judgement is involved, the outcomes of the assessments are also affected by the UI, phrasing, incentived given to the users etc.  

## Prediction interpretation & justification
Limitless explanations can be created. Which explanations are useful? Can the choice of explanation manipulate the user? Based on examples from [3].
### Adding facts (problem solving) preferred over deleting them (logical reasoning)[answer A]
Info on what would make the outcome better preferred to what would make it worse [answer A]
### Perceived fault and causality (how the outcome would be different if the action would have been different) vs perception of blame reduction (how the outcome would be the same if action would have been different)
### Focus on exceptional, controllable, recent, and action-based

## Recommender systems
* Previous choices of the user, e.g. films with favourite actor
* Choices of similar users (collaborative filtering)
* Model features 
* Hybrid 
“(...) previous studies have often evaluated the persuasiveness of the justification and not its justifiability. 
Their experiments showed that for justifiability, feature-based justifications were superior to neighbor-based and user-history-based ones.” [4]
![psychology of explanations](https://github.com/KasiaKozdon/kasiakozdon.github.io/blob/XAI/_assets/2024-05-09-XAI-Explainable-AI/psychology_of_explanation.jpg)


## Counterfactuals
* By definition, cannot be based on data alone (involve scenarios that did not happen)
* Not limited to XAI
  * Liability determination, e.g. does smoking cause cancer?
  * Strategy assessment, e.g. user was shown advert x , and bought the product. Would the user have bought the product if no advert had been shown?
* Goal-dependent
“﻿An explanation of a decision intended to help the user understand the AI system and make inferences about its future performance could best rely on better-world counterfactuals; 
an explanation intended to ensure the user feels a decision was justified or excusable could rely on worse-world counterfactuals.” 

### Desirable characteristics
* Plausible
* Distributionally faithful
* Possible quality metric: Out of Distribution number 
* Sparse (had few feature differences) 
* Proximate (the closest possible world)
E.g. Nearest Unlike Neighbour
* Preferably actionable

## Summary
* Benefits
* XAI as assistance in ML development

## References
0. IBM ["What is explainable AI?"](https://www.ibm.com/topics/explainable-ai)
1. Adadi and Berrada, 2018
2. Doshi-Velez and Kim, 2017
4. Byrne, 2019
5. Biran and Cotton, 2017
6. https://harmanpk.github.io/Papers/CHI2020_Interpretability.pdf
