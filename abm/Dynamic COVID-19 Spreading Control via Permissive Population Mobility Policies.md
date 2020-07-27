# Dynamic COVID-19 Spreading Control via Permissive Population Mobility Policies
## Sequence Diagram Overview
| ![Image of Diagram](https://i.imgur.com/fvl5zuL.png) |
| :--: |
| *Diagram 1* |
Diagram 1 details a sequential overview of the two data sources and four components to the overall COVID-19 Mobility Control project. The NYC Taxi Data will provide information for analysis of travel hotspots, while the CDC Data will act as guide to the spread and containment of the COVID-19 virus. The **Mobility Model** will be in charge of modeling a grid and map of the greater NYC area, as well as updating it with information returned to it. The **Agent Based Simulation Model** will create agents and populate a grid with data from the **Mobility** and **Epidemiological Models**, as well as predict results of trips occuring. The **Epidemiological Model** is in charge of identifying the spread rate and spatial health model of the virus, while the **Mobility Controller** will largely make the decisions based on the createion of the **Agent Based Simulation**.
The steps in order of progression are as follows:
1. The **Mobility Model** uses trip data from the NYC Taxi Data set to create a coordinated model. Meanwhile, the **Epidemiological Model** uses spatial health data from the CDC to make a model of the current proportional spread and chances of infection of the virus.
2. **Agent Based Simulation Model** requests predictions for destinations of trips from the **Mobility Model** as well as the health stats of the location of that destination from the **Epidemiological Model**.
3. **Agent Based Simulation Model** then sends the information of a *Booking Request* to the **Mobility Controller** which sends back either a `0` or a `time` for confirmed booking. 
4. **Agent Based Simulation Model** updates its `tripHistory` vector and sends the new trip data to the **Mobility Model** so that it can add that to itself.
5. **Agent Based Simulation** finally sends the predicted health changes of agents and grids to the **Epidemiological Model** which then sends back an updated agent health status. 
These steps serve as an appropriate guidelines to creating a proper overall Corona Virus 19 Mobility Model.
6. **Agent Based Simulation Model** utilized the Mesa agent based simulation. It creates a Rider Model for isntantiating the riders in the simluation system for 1000 riders and a grid of 50 by 50 , the focus grid for the mobliity project.
7. ** At every step i.e. rider instantiation the rider destination is retreved from the Mobility Model.The grid health is retrieved from the the Epidemiological model. The ride request is sent to Mobility Controller with the rider id, time of hour, grid health, rider health, source and destination. 
8. **The Rider model** utilizes Multigrid to randomly place agents in the Grid. It atached data collectors to retrive the Infection of all agents and agent health as the agent/rider data collector.
9. **A heat map** shows the Grid in terms of the number of active agents.
10. **The infection plot** utilizes the Model datacollector to plot the infection rate on the simualtion.
11. **Future Work:** Agent based model is event based and it can efficiently integrate with Rest based services to the other modules. It can post the mobility data trip data for every succefiul trip and retrieve the agent health based on the epidemiological model. These data can be used at the mobility and epidemiological models to update their models.
12. **Visualizations** can be added to agent based model to showcase the movement of riders with health stats to indicate the health state of the entire grid with respect to riders.
