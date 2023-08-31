Instructions:
the following information describes an epidemiological model called SEIAQFR.
based on the information provided, program the set of ordinary differential equations described using python and any library that is necessary which includes but is not limited to:
1. numpy
2. diffeqpy
3. matplotlib

- make sure that the given set of python code takes into account the differential equations given below along with the information. The code should be able to take a large data set that consists of the number of fatalities, infections, and recovered individuals (and any other data that you would see fit) make sure the code is able to extrapolate the course of the epidemic using the set of different equations below, and predict to reasonable accuracy how the populations of the identified classes below will behave through visual graphs.

Example: (this is a portion of what i would expect from the code)

input into code >
- death count: 1000 @ 4 months
- recovered: 10000 @ 4 months
- total population size: 30000 @ 4 months

output > 
- graph of projected death count @ X months
- graph of projected recoveries @ X months
- graph of projected asymptomatic cases @ X months

Here is the information:

- this program should include code that is able to run in a .ipynb file, commonly called "Jupyter Notebook".

- the ultimate purpose of this model is too:
1. predict disease characteristics
2. impose containtment
3. control and mitigate probably outbreaks through prediction

The model:
this model identifies 7 individual "classes" in a population when modelling a epidemic:
1. susceptible (S): individuals of total population size (N) who may be exposed to the spread of the disease.
2. exposed (E): individuals who have come into contact with infected indiduals at least once. exposed individuals are infected but do not have symptoms and have not been identified as infected. disease is in a latent stage. disease latency is the period of time from time of infection to time of becoming infectious. people go from (S) to (E).
3. infected (I): individuals revealing symptoms and are identified for the infection and have been symptomatically infected. they are infective and spread disease.
4. asymptomatic (A): asymptomatic individuals are infected and infectious. acts as a 'hidden carrier' of the disease. do not show symptoms of the disease and due to lack of rapid tests, are not able to be confirmed.
5. quarantined (Q): individuals confirmed (after medical test) for infection that are either hospitalized or home quarantined. either get well after treatment or die.
6. fatal (F): individuals recovered from the disease, asymptomatic individuals may get automatically recovered without disease detectino and/or treatment. 
7. recovered (R): individuals that did not survive AFTER diagnosis

this model takes the following parameters:
(N): total population size of country/city/community

(beta): average contact frequency. ex: number of people an infected person can infect per day. controls rate of spread + represents probability of disease transmission between a susceptable (S) and infectious (I) person. given population N, with initial susceptable population (S) and initial infected (I), infected individuals impact (S) at a rate of (beta)

(alpha): average time for exposed (E) and contact with infected (I) and showing symptoms of the disease.exposed (E) becomes infectious at a rate of (alpha). the reciprocal 1/(alpha) is equal to the incubation period of the disease. among (E), fraction p developed symptoms and becomes symptomatically (I), and (1-p) remainds asymptomatic (A) after the incubation period 1/(alpha)

(p): fraction of symptomatic infected (I) (1-p): fraction of asymptomatic infected (A)

(gamma): rate of quarantine at home or hospital. the reciprocal (1/gamma) is the infectious period whhere a symptomatic infected person (I)spreads infection.

assumptions:
- they cannot spread infection while quarantined
- all identified individuals will be quarantined (hence probability of 1)

(phi): rate of symptom showing in individuals. asymptomatic (A) contribute to symptomatic infected (I) by developing symptoms (1/phi) days at a rate of (phi). if no symptoms revelaed, they are 'automatically recovered' from the infection, without symptoms or treatment. this is immunity. (A) are removed at a rate of (phi), a fraction of (q) going into automatic remission (immune) and fraction (1-q) become symptomatic (I)

(q): automatic remission/naturally immune/immune (1-q): from (A) to symtomatic (I) (identified by symptoms)

(theta): recovery rate after treatment. quarnatined (Q) get better at a rate of (theta) and (1/theta) represents the average quarantined period in hospital/hom for recovered person during treatment.

(delta): mortality/fatality rate. (Q) get deceased at (delta) rate with probabiity (x), and (1/delta) is average days spend by a patient before death since treatment and quarantine began. (Q) get recovered at a probability of (1-x).

(x): probability of death (1-x): probability of recovery

(R) = beta/gamma. basic reproduction number of the virus determines severirty of spread at any time.

The model makes seveeral assumptions:
- there is a constant population (equal number deaths balance number of births
- homogenous population (each individual has the same opportunity to make contact with other individuals > this means that heavily restricted places (that also skew data points by society type, for example dictatorships) will probably not allow as free movement
- the spread of the virus only accounts for human to human interactions and spread > this discounts any animal to human contact
- individuals affected by the disease either as (A) or (I) can either recover or die > there is no other relevant "state" of their being
- individuals who have recovered cannot be infected again

here are the set of differential equations as a function of time:
1. d(S)/dt = (beta) * S(t) * I(t) / (N)
2. d(E)/dt = (beta) * S(t) * I(t) / (N) - (alpha) * E(t)
3. d(I)/dt = (alpha) * (p) * E(t) + (phi) * (1-q) * A(t) - (gamma) * I(t)
4. d(A)/dt = (alpha) * (1-p) * E(t) - (phi) * A(t)
5. d(Q)/dt = (gamma) * I(t) - (theta) * (1-x) * Q(t) - (delta) * (x) * Q(t)
6. d(R)/dt = (phi) * (q) * A(t) + (theta) * (1-x) * Q(t)
7. d(F)/dt = (delta) * (x) * Q(t)

, where S(t), E(t), I(t), A(t), Q(t), F(t), R(t) are the identified classes mentioned previously as a function of time the epidemic occurs for.

here are 2 additional equations that relate some quantities to eachother, and may be useful:

time for asymptomatic recovery:
1. t_asymp_recovery = 1/(alpha) + 1/(gamma) + 1/(theta)

time for infected recovery:

2. t_infec_recovery = 1/(alpha) + 1/(phi)
