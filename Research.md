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
- dynamic over a long period of time and provides better results in a smaller time period. something about r-square score? basically a proportional value to the dependent variables' variance. in laymens it represents how accurate the variable is over time.- 

> It is at this point I boarded so I had to switch to offline notes but i got the document and model done. I understand the basics now I just gotta code it up and see if it works haha.

##From offline notes:
damn maybe after writing this and creating the code I can publish a research paper with the unversity??????????

from the intro, the gist of the paper is identifying the asymptomatic class to make the measure of their predictive model more accurate.

researchers took into account differet parameters such as latency period, infectivity rate, recovery rate, human immunity, social awareness while calibrating the model in high population areas such as India, Uk, and USA

### the ultimate purpose of this model is to:
1. predict disase characteristrics
2. impose containment
3. control and mitigate probable outbreals

### the model takes known parameters such as:
1. infected count
2. recovered individuals
3. death count
which can be taken and fed into the model to "calibrate" and refine the model for increased accuracy.

DEFINITIONS TO SEARCH UP:
- non convergence growth
- latent period

## SEIAQFR MODEL VARS:
note: during model calibration researchers aimed for the model to be complex and flexible to be as accurate as possible considering a variety of factors and is able to accomodate any impacts that come up

(S) susceptible: individuals of total population (N) who are exposed to the SPREAD of the disease
(E) exposed: individuals who have come into contacy with infected individuals. Exposed individuals are infected but do not have symptoms therefore have not been identified as infected. Disease is in a latent stage. people go from S- > E depending on the amount of times they were in contact with an infected (I) person and the R0, or rate of infection spreading
(I) infected: individuals are revealing symptoms and identified for them and have been symptomatically infected. they are infective and spread disease.
(A) asymptomatic: infected and infectious. acts as a 'hidden carrier' of the disease. do not show symptoms of the disease and due to lack of rapid tests, are not able to be confirmed.
(Q) quarantined: individuals confirmed (after medical test) for infection that are either hospitalized or home quarantined. either get well after treatment or die.
(R) recovered: individuals recovered from the disease, asymptomatic individuals may get automatically recovered without disease detectino and/or treatment.
(F) fatal: individuals that did not survive AFTER diagnosis

## SEIAQFR PARAMETERS:
(beta): average contact frequency. ex: number of people an infected person can infect per day. cnotrols rate of spread + represents probability of disease transmission between a susceptable (S) and infectious (I) person. given population N, with initial susceptable population (S) and initial infected (I), infected individuals impact (S) at a rate of (beta)

(alpha): average time for exposed (E) and contact with infected (I) and showing symptoms of the disease.exposed (E) becomes infectious at a rate of (alpha). the reciprocal 1/(alpha) is equal to the incubation period of the disease. among (E), fraction p developed symptoms and becomes symptomatically (I), and (1-p) remainds asymptomatic (A) after the incubation period 1/(alpha)

(p): fraction of symptomatic infected (I)
(1-p): fraction of asymptomatic infected (A)

(gamma): rate of quarantine at home or hospital. the reciprocal (1/gamma) is the infectious period whhere a symptomatic infected person (I)spreads infection. 

assumptions:
- they cannot spread infection while quarantined
- all identified individuals will be quarantined (hence probability of 1)

(phi): rate of symptom showing in individuals. asymptomatic (A) contribute to symptomatic infected (I) by developing symptoms (1/phi) days at a rate of (phi). if no symptoms revelaed, they are 'automatically recovered' from the infection, without symptoms or treatment. this is immunity. (A) are removed at a rate of (phi), a fraction of (q) going into automatic remission (immune) and fraction (1-q) become symptomatic (I)

(q): automatic remission/naturally immune/immune
(1-q): from (A) to symtomatic (I) (identified by symptoms)

(theta): recovery rate after treatment. quarnatined (Q) get better at a rate of (theta) and (1/theta) represents the average quarantined period in hospital/hom for recovered person during treatment.

(delta): mortality/fatality rate. (Q) get deceased at (delta) rate with probabiity (x), and (1/delta) is average days spend by a patient before death since treatment and quarantine began. (Q) get recovered at a probability of (1-x).

(x): probability of death
(1-x): probability of recovery

(R) = beta/gamma. basic reproduction number of the virus determines severirty of spread at any time.

NOTE: after reading through VARS + PARAMETERS, i realize now why this model is effective for certain scenarious. India, UK, and USA all reported their COVID-19 infection numbers and provided data more or less willingly and transparently unklike China. This makes sense now that I'm writing and researching this but the data makes all the difference. Chinas data is garbage hence this model won't work for it.

### parameter estimation
the number of deaths (F), recovered (R), andquarantined (Q) and infected cases (I) are all available in Government published stat websites. Assume the government doesn't screw with numbers.

These numbers mean that we have initial:
(I0, R0, and F0) (infected, recovered, dead)

using these numbers on hand, we can calculate:
(E0, Q0, and A0) (exposed, quarantined, and asymptomatic)

we calculate according to the initia spread of disease in the region and time in which it spread.


## other notes
Using the vars and parameters and interaction chart, researchers used system of nonlinear ODE for this new SEIAQFR model.

## assmptions
The model makes seveeral assumptions:
- there is a constant population (equal number deaths balance number of births
	* most likely have to say that the model must be generated on an annual basis for prediction of a disease due to changine population numbers
- homogenous population (each individual has the same opportunity to make contact with other individuals
	* this means that heavily restricted places (that also skew data points by society type) will prob not allow as free movement

- the government from which the data is collected doesnt screw with numbers. This is a decently big factor just because of the amount of countries this limits the model to.
	* this is also shown by the relatively small amount of countries this was tested on.

- the spread of the virus only accounts for human to human interactions and spread
	* this discounts any animal to human contact

- individuals affected by the disease either as (A) or (I) can either recover or die
	* there is no other relevant "state" of their being

- individuals who have recovered cannot be infected again
	* consider amending this??????????? what about something like the common flu, where some people catch it on an annual basis
	* this is 
