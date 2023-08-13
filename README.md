# COVID 19 Analysis and Prediction
 Here is a project I did back in grade 12. Takes a look at COVID-19 data at the time and predicted death rates, recovery rates, and stuff.

 Used an epidemiology model called the SIR model, developed by some people called Kermack and McKendrick in the 1920s. This model considers an epidemic without vital factors such as death rates, birth rates, etc. The SIR model considers only 3 classes of people: susceptible, infected, and recovering.
 
After taking a look at my previous code, I realized how flawed it was (haha) so I guess I'm going back and redoing my project such that it:
1. makes more sense
2. takes into account a greater variety of factors (include vital dynamics)

Here goes nothing.


## 2023/08/11
Im starting off by refreshing what I need to learn. I'm going to choose a new model of epidemiology: one that takes into account vital dynamics and more factors that would be able to give a more accurate model.

I found an article
> https://bmcinfectdis.biomedcentral.com/articles/10.1186/s12879-022-07472-6

and i also found what types of models i can use:
1. stochastic (random)
2. deterministic/compartmental
