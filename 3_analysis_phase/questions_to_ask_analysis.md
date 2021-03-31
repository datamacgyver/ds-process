# Dataset Assumptions
1. What does the way the sampling was done assume about the future data? In which
cases will these assumptions be wrong?

2. Will all of the features available in the dataset be available in the future?
Will any of them be calculated differently (and if so, will you know about it)?

3. Did characteristics of your dataset change over the time it was collected (e.g. 
different mix of genders, climate change, before/after people had cellphones)? Did 
you limit your dataset to periods of time during which the characterstics were 
similar to today?

4. Often your dataset is sampled to reflect a phenomenon in real life. What are the
limitations of your sampling procedure? What can’t your sampling see?

5. Given that your data is collected over time, are there any low frequency 
phenomenons that might have been missed? Make sure you collect your data for a 
long enough time period.

# Preprocessing
1. Make sure you used the same preprocessing procedure for your train and for 
your test

2. Did you normalize before modeling according to the best practice of that 
algorithm? (This doesn’t matter if model is decision-tree-based)

3. If you normalize the data: Did you calculate the parameters based only on 
the training data? If not, is the calculation repeatable in the production 
environment?

4. Is your scaling method sensitive to anomalies? Make sure there isn’t a 
single sample that strongly affects your scaling

5. Do you have any delta-like distribution for your features? If model isn’t 
decision-tree-based, consider using a non-linear scaling method (log, precentiles) 
to prevent such situations

# Leakage and Bias (excluding time related issues)
1. Does the index contain any information?

2. Does the index, or any feature calculated while using the index, appear in 
the final features (before modelling)?

3. Train a simple decision tree or a random forest on your data and look at 
the feature importances it produces. Make sure that there isn’t a suspiciously 
important feature — that might imply a leakage.

4. Was any of your data generated? If so, check if it’s possible that 
generation was done differently for different classes/values of the label.

5. Did you collect samples of your data to train the model? If so, check if 
this was done differently for different classes/values of the label (e.g. 
positive samples from one city and negative from a different one).

6. How many experiments were run to obtain the final evalutation on the test 
set? If more than 5, this score may potentially include “leaderboard likelihood” 
(a term which I heard from Seffi Cohen  and  Nir Malbin for choosing your Kaggle 
final submission based on too many submissions to the public leaderboard).

7. Given that you expect your train segment to resemble your test segment, how 
different are they? Try training a simple model to tell them apart — If it’s 
significantly successful, this may be a source of leakage.

8. Can you split your data into train-test segments differently? If so, try 
doing so and make sure you get the same results.

9. Does the model performance seem reasonable/possible? Is there some known 
unavoidable error threshold that you have passed?

# Causality
1. How long after your predictions do you expect to obtain new labels in
the future? Is this true for all possible values of the label? Did you assume 
otherwise while planning your system?

2. Does the training set include any information from the future?
(Specifically from the timeframe of the dev/eval/test set or later)

3. Do any of the features include information that neccessarily comes
from the future? (e.g. moving average with a window extending both forwards 
and backwards)

4. When predicting “far into the future”, be careful when using a “rolling 
model”. Make sure that you use it as a “rolling model” during training.

# Loss Function/Evaluation Metric

1. Does the loss function in the code measure what it should be measuring?
(e.g. what was previously discussed)

2. Does the loss function match the evaluation metric? If not, is the connection
between them monotonous?

3. Does the evaluation metric match the business metrics (including for all
edge cases)? If not, can we add post-processing to take care of the edge cases?

4. For an ensemble or model with complex post-processing: Does minimizing the
different loss functions ensure the optimization of the final output?

5. For Neural Nets: Did the loss function really stop improving? Is it smooth
and flat towards the end of the training, or does it exhibit different behaviors
(noisy, still going down)?

6. For Neural Nets: Does the training process look reasonable? Do the train
and validation over epochs graphs exhibit standard behavior?

7. For custom/uncommon loss functions: What kind of anomalies is your loss
function sensitive to? Make sure it doesn’t get extremly high values or have 
unbounded gradients for specific data samples.

# Overfit
1. Does changing the random seed change the results dramatically?

2. Does evalutating your results on a random sample of the test set obtain 
the same results?

3. Did you use a few different folds while evaluating your model? (While 
making sure the dev/eval/test set don’t appear in any of them)

4. How did you preform hyper parameter tuning/feature selection? make sure 
you used the training set only.

5. Look at your train and test graphs as a function of a complexity 
parameter (training epochs, depth of tree, ect.). Use it to make sure you aren’t 
overfitting on your training set.

6. Can you obtain similar results while reducing the number of parameters in 
your model? (Note that this point is conterversial from an academic point of 
view, especially for Neural Nets)

# Runtime
1. Can you obtain similar results while reducing the number of features in 
your model? (Similar to the previous point but a bit different)

2. Which feature takes the longest to calculate? How much of the runtime is 
spent for this process? Is it’s addition to the accuracy worth the runtime?

3. Which hardware did you assume you’ll have in production? Assuming you’re 
using a machine that costs half the price, is there still a way to obtain similar
results?

4. For an ensemble: How much better is this than your single best model?

# Stupid Bugs
1. Was the original index column ever deleted? If so, which mechanism was used to 
make sure the order stayed the same?

2. Were the names of the columns ever removed? If so, which mechanism was used to 
make sure the order stayed the same?

3. Does the index column of the label completely match the index column of the 
features?

4. Were there any merges/joins during the preprocessing phase? If so, did any of 
them: a. Create a lot of nulls. b. Change the number of rows to a number that 
wasn’t expected

5. Was any dictionary loaded to memory during preprocessing? If so, is it the 
correct version of the dictionary?

6. Is the model you are using the model that yields the reported results? (i.e. 
make sure you are using the correct weight file)


# Trivial Questions that Must Be Asked
1. Is there any important library that you didn’t install and experiment just 
because of technical issues/laziness?

2. Is there any feature that someone else in the organization is creating 
especially for you? If so, did you check if you can do without it?

3. Did you compare with an intelligent benchmark which doesn’t use machine 
learning? (e.g. average value, most common class, random labels with the same 
distribution as the training set)

