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

i found this document that explained the SEIAQFR model:
> https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9353108/#:~:text=Here%20we%20have%20proposed%20a,transmission%20and%20quarantine%20of%20patients.
> since this isnt a research paper and just a project im gonna cite as many papers as i need its not gonna be peer reviewed.
> my thoughts are i just wanna do it not just make a paper.
> i wanna make it clear to myself and i guess whoever is crazy enough to actually read this that my goal is to program a more accurate model using python and learn a couple things on the way. would be cool to use ai/ml but thats another can of worms.

upon reading this paper im now realizng that using this model will be really really hard cuz apparently its a new model. this may take a while to understand.

## Variables:
first things first, gotta understand the variables...

R(0): "R-naught", or reproductive rate
- dynamic over a long 
