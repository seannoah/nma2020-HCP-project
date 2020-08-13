# Neuromatch Academy 2020 - Ethereal Pony Group Project

[Video Presentation](https://youtu.be/20iHL1mIigU)

## Overview

**Project Topic:** Detecting Boredom in the MRI Scanner

**Scientific Question:** When someone is supposed to be performing a cognitive task but they are momentarily bored and disengaged, does their brain activity look like that of a resting state brain?

**Brief scientific background:** A large body of research suggests that when a person is in a resting state, i.e., passive and not instructed to perform a cognitive task that requires deliberate effort, there is a specific network of areas in their brain that activate to a greater degree than other areas. This network has been called the Default Mode Network (DMN). Boredom, although not identical to the conventionally defined resting state, shares features with the resting state, and therefore might evoke discriminable patterns of activity in the default mode network. Unlike resting state, boredom is generally defined to be an intrinsically aversive condition. Boredom is detrimental to effective behavior, and chronic boredom can negatively impact mental health. In neuroimaging experiments, boredom can diminish effect sizes and reduce statistical power, adding an additional layer of noise to already noisy neuroimaging data, and effectively increasing the cost of running neuroimaging experiments. Several lines of neuroscientific research into boredom suggest that the brain areas activated when a person is bored overlap closely with the DMN. If boredom does ilicit identifiable DMN activity, then it could potentially be detectable on an individual basis using the individual's resting state data as a search template. Detecting boredom in fMRI data could provide a principled way to exclude segments of data from analyses, improving statistical power. Detecting boredom is also an interesting tool for studying the neural mechanisms of sustaining attention during cognitively demanding tasks, as boredom can be considered a lapse of attention or capture of attention by an internal distractor.

**Proposed Analyses:** Train a classifier on a subset of the openly available Human Connectome Project (HCP) dataset – just BOLD data from the resting state scan condition and the working memory (WM) task scan condition. To verify that prediction probability is a meaningful measure, we will first assess the ability of the classifier to decode scan condition from unlabeled test data. If the classifier can decode task condition from BOLD data with high accuracy, then prediction probability for any given input datapoint will provide a useful continuous measure of how typical that datapoint is of either condition category. Then, we will relate response accuracy – a behavioral measure of WM task performance – to the decoder's prediction probability for each datapoint in the WM task dataset. 

**Predictions:** In this project we operationalize boredom behaviorally as WM task trial non-responsiveness: When a participant is bored, potentially mind-wandering or otherwise disengaged from the WM task at hand, they will not be paying attention to the task and therefore miss the cue to input a response. We therefore predict that given BOLD data belonging to a WM task trials where no response was recorded, the trained classifier will predict with high probability that the trial belongs to the resting state condition, relative to a similar prediction measure obtained from a WM task trial that elicited a correct behavioral response. 

## Results
* A range of classifier algorithms can be used to decode task state (WM vs. rest) from parcellated cortical BOLD signals.
* Decoding accuracy reaches ~90 percent accuracy
* Accurate decoding can still be performed when the original 360-dimension dataset is transformed into a space of a small number of principle components, with decoding accuracy plateauing at about 75 components.
* WM task trials in which participants did not enter a behavioral response were associated with significantly greater rest state prediction probability than correct-response trials.
* Somewhat counterintuitively, Incorrect-response WM trials were linked to a lower rest state prediction probability than correct-response trials. 
* In a functional connectivity analysis, no-response WM trials showed greater connectivity between canonical DMN areas than correct-response and incorrect-response trials, strengthening our interpretation that behaviorally operationalized boredom is linked to DMN activity. 


## Questions
* Can we detect when someone is bored in the fMRI scanner?
  * Q1: Can we use a classifier to decode task state (rest vs. WM) with significantly above-chance accuracy?
  * Q2: What kind of classifier is best for this analysis?
  * Q3: Can the classifier still perform well on a reduced-dimensionality transformation of the original fMRI data?
  * Q4: What is the relationship between WM task behavioral performance and prediction probability that a WM task datapoint belongs to the resting state condition?
  * Q5: If we can identify signs of boredom in WM fMRI data, what will functional connectivity in the bored brain look like?

## Predictions
* Q1: Because of the large body of resting state research that has identified the DMN as uniquely active in the brain during rest, whole-brain resting state BOLD data should be clearly discriminable from whole-brain WM task BOLD data, even though the BOLD data in the HCP dataset was preprocessed and downsampled to 360 cortical parcels.
* Q2: Logistic Regression or K Nearest Neighbors should work well because in general they train quickly compared to more complicated classification algorithms, and the decision boundary should be easily calculated because the two brain states being decoded are so different.
* Q3: We predict that a reduced-dimensionality dataset will still capture most of the important variance that can be used to discriminate the two task states, because fMRI data is intrinsically noisy and so there are probably many sources of variance that are independent of task condition.
* Q4: We predict that WM trial non-response will be at least partially attributable to boredom, therefore, the no-response trials will have a greater resting state prediction probability assigned by the classifier.
* Q5: We predict that no-response trials will have greater functional connectivity between brain areas that are canonically part of the DMN.

## Methods
* A range of classifier algorithms: logistic regression, K nearest neighbor, support vector machine, random forest, decision tree, QDA, multilayer perceptron. 
* K nearest neighbor classifier algorithm to obtain prediction probability measures.
* PCA for dimensionality reduction.
* Correlation coefficient to calculate functional connectivity across brain areas.

## Next Steps
* Using functional connectivity data as input to classifier, instead of BOLD amplitudes.
* Correlating classifier measures with other physiological measures, including eyetracking and heartrate.
* Evaluating boredom propensity (predictive model) or prevalence (classification model) across demographics, tasks, and pathologies.

## References
* Rajan A, Meyyappan S, Walker H, Samuel I B H S, Hu Z, Ding M. 2019. Neural mechanisms of internal distraction suppression in visual attention. Cortex 117: 77-88
* Wen X, Liu Y, Yao L, Ding M. 2013. Top-Down Regulation of Default Mode Activity in Spatial Visual Attention. The Journal of Neuroscience 33(15):644-6453
* Moreira P S, Marques P, Magalhães R. 2016. Identifying functional subdivisions in the medial frontal cortex. Journal of Neuroscience, 36(44): 11168-11170
* Van Den Heuvel M P and Pol H E H. 2010. Exploring the brain network: a review on resting-state fMRI functional connectivity. European neuropsychopharmacology, 20(8): 519-534 
* Danckert J and Isacescu J. 2017. Danckert & Isacescu fMRI of boredom replication. 
* Greicius M D, Krasnow B, Reiss A L, Menon V. 2003. Functional connectivity in the resting brain: a network analysis of the default mode hypothesis. Proceedings of the National
Academy of Sciences, 100(1): 253-258. 
* Eastwood J, Frischen A, Fenske M, Smilek D. 2012. The Unengaged Mind: Defining Boredom in Terms of Attention. Perspectives on Psychological Science, 7(5): 482-495.


