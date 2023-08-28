Instructions:
the following information describes an epidemiological model called SEIAQFR.
based on the information provided, program the set of ordinary differential equations described using python and any library that is necessary which includes but is not limited to:
1. numpy
2. diffeqpy
3. matplotlib

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

