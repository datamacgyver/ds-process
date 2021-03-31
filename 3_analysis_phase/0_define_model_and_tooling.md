# Define Output Artefact and Tooling Needs

## Tooling
Does either the analytical output (ie the model or dash) require any special 
hardware (or software/tooling) to either train or deploy? If so these may need requesting or setting 
up. This can include permissioning etc for deployment use, which can take a while. 

## Artefact? 
What do we mean when we talk about "the artefact"? If we were talking about a 
model then we would need to define what we mean to deploy: The feature pipeline? 
Just the trained model? What about the monitoring procedures? 

How we do this will evolve as we do, at present we are not really in a 
position to think much on this other than "How hard do you think this will 
be?". One to think upon and iterate over as you dev.

The pipeline needs should not necessarily control the modelling process, but
the process should be mindful of it. We don't want to build a monolith 
that's impossible to deploy! You should have thought about this in earlier phases
but now is the time to formalise these thoughts. 

### A Note for Future
Once we have a better idea of this, it would be more performant to setup a 
pipeline at this stage (preferably from a template) and then use it for 
training/analysis. In doing so you'd remove pain (and possible failure) from 
your productionisation phase. 

Keep this in mind if you are the first person to get here, build what you need
with an eye on re-usability. 