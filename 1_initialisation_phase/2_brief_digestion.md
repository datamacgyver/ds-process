# Brief Digestion

This is where you put the notes from teh client into Data Science speak! You 
may also be required to do some high level data exploration to confirm the data
are what they are supposed to be, that predictors can be made and to identify any
data risks or assumptions. 

The notes below will help you in your thinking but I WILL ALSO ADD A LINK TO THE 
ANALYSIS CHECKLIST THAT MAY INDICATE SOME THINGS TO CHECK. 

## KPIs
Define hard/soft KPIs as appropriate (it depends on the project and the output; 
human assisting tools are often softer). How will these be evaluated (i.e. SME or metric?).
Soft metrics may be evaluated through stakeholder review, which is fine. 

**Hard:** 
> As a salesperson, want to be able to detect 70% of my customers at risk of churn, 
> with a false positive rate below 20%. 

**Soft**
> As a salesperson, I want to be able to quickly identify which of my customers have decreasing 
> spend in crop Protection so I can increase my total sales.

## Potential Approaches
* What high-level approaches could we use (e.g. unsupervised clustering vs boosted-tree-based 
classification vs probabilistic inference)?. To do this you need to have a clear idea of the 
deliverables! 
* What (if anything) already exists? Can it be re-used or modified?  
* Don't be afraid to seek input from non-DS resources (such as your stakeholders). They may 
have ideas or assumptions that are of use. 

## Scope
What does the MVP look like? What does the final solution look like? How do we get from 
A to B?

Make sure the KPIs match this, is there a "minimum for use" KPI (ie 60% accuracy) and a 
"preferred" KPI (say, 80% accuracy?). If a KPI/requirement seems ridiculous then can we 
re-frame the problem? 

## Data
* Are the data up to the task? Brief data exploration/schema understanding may be required. 
* What data do we need? From where? Do they need obfuscating? Have we requested access? 

## Bureaucracy
* Do we have a vague estimate of effort (Days/weeks/months) to MVP? To completion? 
* What risks, assumptions and dependencies are there? Can we monitor or remediate? 

*Based on the above, is the project possible? If not, how can we reframe it to be a soluble problem?*  