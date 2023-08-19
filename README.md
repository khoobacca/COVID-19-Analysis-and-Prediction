# COVID 19 Analysis and Prediction
 Here is a project I did back in grade 12. Takes a look at COVID-19 data at the time and predicted death rates, recovery rates, and stuff.

Used an epidemiology model called the SIR model, developed by some people called Kermack and McKendrick in the 1920s. This model considers an epidemic without vital factors such as death rates, birth rates, etc. The SIR model considers only 3 classes of people: susceptible, infected, and recovering.
 
After taking a look at my previous code, I realized how flawed it was (haha) so I guess I'm going back and redoing my project such that it:
1. makes more sense
2. takes into account a greater variety of factors (include vital dynamics)

Here goes nothing.

Im starting off by refreshing what I need to learn. I'm going to choose a new model of epidemiology: one that takes into account vital dynamics and more factors that would be able to give a more accurate model.

I found an article
> https://bmcinfectdis.biomedcentral.com/articles/10.1186/s12879-022-07472-6
> which basically says different models sheds light on epidemics in different geographical areas.

and i also found what types of models i can use:
1. stochastic (random)
   a. manipulating the odds
2. deterministic/compartmental
   b. manipulating the strategy
> https://www.aimspress.com/article/doi/10.3934/mbe.2021050?viewType=HTML#:~:text=The%20above%20results%20highlight%20the,extinction%20when%20R%200%20%3E%201%20.
> basically used the SEIR model (updated SIR model) to analyze and predict rates, but isnt comprehsive. Does not consider asymptomatic, symptomatic, hospitalized individuals and different age groups.
> not comprehensive

### Basically,
any mathematical model has to make assumptions. as predictions are made the model can be adjusted to fit different scenarious

Based on this very general prelim info, I want to:
1. find a model that can predict the course of a disease based on previous data points (trends in data)
2. use a learning model to predict the course of a disease better.

This will require:
1. python, numpy, matlab, pandas
2. data scrubbing + data analysis
3. developing a learning model

> ## thoughts:
> after thinking about this more, im realizing the ML is a stretch. If i pursue that option ill have to create one, train one, and integrate it with a model that id code.
> maybe i can just code the mathematical ep model using py libraries, and research how i can use ai to enhance it?
> maybe use ai to take a look at the effectiveness of the model?
> the questions i then would need answered is:
> 1. what is the most comprehensive model of an epidemic
> 2. what does the model mean? understand the model
> 3. how do i code it? (python, numpy, matlab, pandas)
> 4. can i make this look pretty and graph it out? (matplotlib)
> 5. where can i find data to test if it works thru backtests/trials with historical data?
> 6. is it possible to use ml or make a model that predicts an epidemic better?
> 7. can i feed a learning model some data and ask it to predict what happens?
> 8. how do i create such a learning model? how do i even start making an ml model? is this somethign that is gonna hard AF to do? (probably)

lots of thoughts, time to do. ill update these thoughts in order progressing from general overview of what i need to specifics.
