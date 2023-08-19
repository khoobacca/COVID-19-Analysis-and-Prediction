# Models of Epidemiology

1. Stochastic (random)
2. Deterministic/Compartmental

- Typically keeps track of multiple "compartments" of peoples (recovered, exposed, infected, etc), hence "compartmental" models
- Uses system of ordinary diff equations (ODE)

Kermack-McKendrick compartmental model of the 1920s only took into account 3 compartments of people: suscptible, infected, recovering.

an updated compartmental model I found based on the old SIR model (taking into account a greater variety of factors):

## SEIAQFR
Susceptible
Exposed
Infected
Asymptomatic
Quarantined
Fatal
Recovered

obviously, this model is a more accurate/encompassing model due to the sheer amount of variables (3 var -> 7 var) that it accounts for. which also means its gonna be an even greater pain in my ass to understand lmao. here goes nothing.

i found this paper that explained the SEIAQFR model:
> https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9353108/#:~:text=Here%20we%20have%20proposed%20a,transmission%20and%20quarantine%20of%20patients.
> since this isnt a research paper and just a project im gonna cite as many papers as i need its not gonna be peer reviewed.
>
> i wanna make it clear to myself and i guess whoever is crazy enough to actually read this that my goal is to program a more accurate model using python and learn a couple things on the way. would be cool to use ai/ml but thats another can of worms.

upon reading this paper im now realizng that using this model will be really really hard cuz apparently its a new model. this may take a while to understand.

> more thoughts:
>
> the more i look at this document the more im thinking shit theres so much to learn lmao. anyways, the paper says that the R-square score of the SEIAQFR model was a 0.95-0.99 for infection prediction and 0.90-0.99. in other words its really fucking good. the more variables the better, i guess.
>
> introduction starts off with some background about what viruses havedone to humans. simply put, viruses destroy. viruses are bad. we can use disinfectants to kill viruses. interestingly, by using disinfectants, we can (as the name suggests) prevent new infections.
>
> the authors also talk about different protocols we've used (masks, vaccines, social distancing, lockdowns, sanitizations, quarantining, etc). by taking thes measures, we werew able to start actually tracing contacts of infected people.
>
> before COVID and at the beginning, people used the SEIR model (another model based off the og SIR model) this was found to be ineffective because of the amount of asymptomatic people. this caused mathematicians to ball out and develop new models, one of which being the SEIAQFR model.
>
> because t

## Variables:
first things first, gotta understand the variables...

R(0): "R-naught", or reproductive rate
- dynamic over a long period of time and provides better results in a smaller time period. something about r-square score? basically a proportional value to the dependent variables' variance. in laymens it represents how accurate the variable is over time.
