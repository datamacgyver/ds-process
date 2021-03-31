# Questions to Ask

*I put this together using various blog posts and internal logic, happy to have it 
modified - Rob* 

Below details some potential questions to ask of the data and the solution. They 
are neither required nor exhaustive but they should help guide you in your 
exploration.

## Data Properties
* How was the generated? How was it samples? Was it updated?
    * E.g. 10% of last month data was sampled uniformly from each of the existing five clients.
* What noise, sampling bias and missing data did this introduce?
    * E.g. one of the clients only integrated with our service two week ago, introducing a down-sampling bias of his data in the dataset.
* Can you modify sampling/generation to reduce or eliminate noise? Sampling bias? Missing data?
    * E.g. either upsample the under-sampled client by a factor of two, or use data from only the last two weeks for all clients.
    * Can you explicitly model noise, independently from an approach?
* If the dataset is labeled, how was it labeled?
* What label bias did this introduce? Can it be measured?
    * E.g. the label might come from semi-attentive users. Labelling a very small (but representative) set by hand using experts/analysts might be tractable, and will enable us to measure label bias/error on this set.
    * Can you modify or augment the labelling process to compensate for existing bias?
* How similar is the initial dataset to input data expected in production, structure and schema-wise?
    * E.g. the content of some items changes dynamically in production. Or perhaps different fields are missing, depending on time of creation, or on the source domain, and are later completed or extrapolated.
* How representative is the initial dataset of production data?
    * E.g. The distribution of data among clients constantly changes. Or perhaps it was sampled over two month of spring but the model will go up when winter starts. Or it might have been collected before a major client/service/data source was integrated.
* What is the best training dataset you could hope for?
    * - Define it very explicitly.
    * - Estimate: By how much will it improve performance?
    * - How possible and costly is it to generate?
    * E.g. tag the sentiment of 20,000 posts using three annotators and give the mode/average score as the label of each. This will require 400 man hours, expected to cost two or three thousand dollars and is expected to increase accuracy by at least 5% (this number is usually extremely hard to provide).

## Approach 
### Assumptions
* Is the data quality/source expected to remain static over time? What is the expected variability? What about for new clients? 
* What assumptions does each approach make on the data / data generation process / the phenomenon under study?
 	* Is it reasonable to make these assumptions about your problem? To what degree?
 	* Can you associate violation with decreased efficacy? 
* Can these assumptions be validated independently?
* Any edge/corner cases which violate these assumptions?
* Here are some examples of some very strong and commonly implicit assumptions approaches make:
 	* Each feature follows a Gaussian distribution.
 	* Time series are realizations of a stationary process.
 	* Features are strictly independent (e.g. Naive Bayes assumes this).
 	* Separability of the measurements of different components in the system being measured.
* Do we have enough data to train our chosen model? Will that always be the case? 
	
### Past Experience
* What experience do you have applying this approach, whether in general or to similar problems?
* Did you find any published (e.g. in a blog post or an article) success/failure stories of applying this approach to similar problems?
* Did you reach out to peers for their experience?
* What lessons are to be learned from the above?
* If this project is an attempt to iterate and improve upon an existing solution: What solutions were used to solve this problem so far? What were their advantages and from what issues did they suffer?
	
## Objective Alignment

### For supervised learning:
* Which loss functions can be used when fitting model parameters? How do they relate to project KPIs?
* Which metrics can be used for model selection / hyperparameter optimization? How do they relate to project KPIs?
* What hard constraints should be added to reflect KPIs?
	
### For unsupervised learning methods:
* What measure does the method optimize?
* Are there edge cases that satisfy the metric but not the KPI?

### For non-modelling tasks: 
* How do our KPIs align to the problem statement? How will they be measured?
	
## Implementation
* Are there implementations of the approach in a language currently used in your production environment?
* Is the implementation up-to-date? Consistently supported? In wide use?
* Are there successful uses of this specific implementation by companies/organisations similar to yours? On problems similar to yours?

## Cold Start & Domain Adaptation
* How fast will new clients/categories/countries/domains are expected to reach the minimal information requirements of each approach?
* Can a general model be expected to perform well for them, at least as a starting point?
* Is there a way to adapt an already-fitted model to a new domain? Is this expected to yield better performance than training from scratch? Can this be done faster/cheaper than training from scratch?
	
## Noise/Bias/Missing Data Resilience
* Does the approach handle noise in the data? How?
 	* Does it model it specifically?
 	* If so, consider: How applicable is the noise model to the noise generating process in your problem?
 	* For anomalies/prediction/causality/dynamics: Does the approach model exogenous variables in the system?
* For supervised and semi-supervised methods:
 	* How sensitive is each approach to bias in labelling?
 	* What are the implications of a biased model in your case?
 	* Are generic bias-correction techniques applicable to the approach?
* For all methods:
 	* How does each approach handle missing data, if at all?
*   How badly is performance expected to degrade as missing data increases, in each case?