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

when i was coding it turns out I need to use Julia, which is kindof a pain in the ass to install into vscode, so I ended up using a different diff equation solver (changed from diffeqpy to odeint using scipy)

### data scrubbing/analysis:

now that ive made the basic program for solving the diff equations, i have to collect some data, preprocess it, and optimization.
this involves:
- normalizing, filtering, and transforming the data.

i can get this data from a government website... will figure out how to do this once i get this code working
maybe import a set of data into an array?... file streaming? data set will prob be too big so i'll see how it works.

i just tested my code... i need some data now. im not going to worry abount scrubbing before i upload into an array just so i can see how this works... ill try and find some data in a csv format so i can parse it into the array in my code so i can actually do things with the data.

im going to use pandas and load the data from someplace i find online. here is the source: 
> https://www.kaggle.com/datasets/imdevskp/corona-virus-report?resource=download
> https://www.worldometers.info/coronavirus/
> https://health-infobase.canada.ca/covid-19/current-situation.html

edit: damn i found the website kaggle. really fucking cool lmao. i heard of it before but this website is so helpful ill just link it and upload the data to this project file.

edit: i found another source on worldometer with some covid data I can use. I also found a website on the official canadian website with a csv with daily number of confirmed spots taken in hospital beds, which represent quarantined individuals. notice the total number of patients hospitalized does not match the total number of identified persons that day. obviously. lmao. we dont have enough space so i have to assume they actually quarantined at home? but no guarantee on that. so many moving parts but at least have more data. anyways ill download the csv and start graphing it in my code.

This is so helpful... there is covid-19 infection information from everywhere. i mean every single country, every single place, everywhere. ill graph this out first and see what i can do with this.

## heres the plan for now:
im updating this as i go along but here:

# what i have:
- code to solve the SEIAQFR model solved using odeint
- code to predictively model/graph the epidemic
- data from every major country across the globe.

# what i need:
- code to scrub the data
- scrub the data
- model of the actual situation
- code to analyze real world data after graphing and file streaming to find more accurate disease parameters for a more accurate SEIAQFR model to predict more accurately. basically to help fine tune the model even more.
- ml model lmao??

# the overall goal:
1. an actual model + graph using DATA of the COVID-19 epidemic that provides more accurate parameters for the predictive model using straight math and the ai
2. an predictive model + graph using SEIAQFR of the COVID-19 epidemic (timeline can be adjjusted to predict epidemic)
3. an predictive model + graph using MACHINE LEARNING of the COVID-19 epidemic (timeline can be adjusted to predict epidemic)

i want to predict a disease with this model or machine learning USING the power of computing.

## more updates

DAMN i just uploaded a shit ton of data... now i gotta sift through it and see whats useful and what isnt
also, this git project file is really messy so i need to clean it up as well

Another realization... i can analyze real world data for this disease for more accurate parameter values for use within my model. ill add this to my plan. im kind adoing this as i go but cest la vie. im learning i guess haha

## file streaming and csv parsing
started to make some arrays to load the data into

## more things to do... 2 months later
so school went really well. started on my drone design team and got a research position at CRN (composites resarch network) among things that I did. I still want to finish this project so during winter break when im not applying to internships for summertime, I'll be working on an ecommerce project with my friend, and building a portfolio website maybe (goes hand in hand with ecomm, cuz we need a website anyways so better to practice).

believe it or not, ecommerce and starting an online business is significantly easier than this math stuff. never really my strong suit but i still want to finish it.

...

after catching up to where I left off, I'm going to end up analyzing the real world data I left off with and finding parameters for my own SEIAQFR model to be based upon. for me to do this, I'm going to scrub the data.

Ill just start with that right now, as I've already plotted the real world data and made a basic SEIAQFR model with assumed values and constants/parameter values. If the initial conditions and the parameters aren't correct then my model will be massively off.