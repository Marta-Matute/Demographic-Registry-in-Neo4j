# Neo4j Project: Demographic Registry
Neo4j is a graph database management system with libraries that contain many graph algotithm. This is particularly useful to analyse any given database and draw conclusions from it. This repository is made up of all the files used and created for a University Project on Non-Relational Databases. In particular it explores the different types of queries that can be made, as well as some data analysis on the graph using [GDS](https://neo4j.com/docs/graph-data-science/current/algorithms/). More on the specific questions asked later.

[Cèlia Martínez, NIU: 1569504, Github user: celia-m15](https://github.com/celia-m15)

[Marta Matute, NIU 1496672, Github user: Marta-Matute](https://github.com/Marta-Matute)

[Goretti Peña, NIU: 1566866, Github user: gorettipena](https://github.com/gorettipena)

[Judit Ugas, NIU: 1569163, Github user: Juditu](https://github.com/Juditu)


## Introduction
The context of this project is based on the existing and ongoing research [XARXES](http://dag.cvc.uab.es/xarxes/) by the Computer Vision Center at Universitat Autònoma de Barcelona. We will be using the same data as them, given to us in the form of .csv files, that we will firstly convert into Neo4j graphs. The second exercice will be to answer ten queries, to check that the graph and its properties are properly built. Finally, the last exercice will focus on the use of GDS to analyse and better understand the structure of our data.

## Data structure
Let's firstly have a look at the graph's structure, once created. We will have two different types of nodes "Persona" (Person) and "Habitatge" (Home).
- A node of type "Persona" has the following properties:
  - "Id": Id given by the .csv files (different from the automatically created id by Neo4j)
  - "Cognom" (last name): First family name
  - "Segon_Cognom" (second last name): Second family name
  - "Nom" (name): Given name
  - "Any" (year): Year from the registry where this person was first encountered.
- A node of type "Habitatge" has the following properties: 
  - "Id_Llar" (home Id): Id given by the .csv files (different from the automatically created id by Neo4j)
  - "Any_Padro" (Registry Year): Year from the registry where this home was first encountered.
  - "Carrer" (Street): Name of the street where home is located
  - "Numero" (number): Door number of the house. 
  - "Municipi" (municipality): Name of the municipality where the home is located.
- A relationship of type "VIU" (lives in), which connects a person to the home where they live, has the following properties: 
  - "Any" (year): Year in which the person lived in the house.
- A relationship of type "SAME_AS", which connects two nodes of type "PERSONA" that correspond to the same individual, has no properties.
- A relationship of type "FAMILIA" (family), which connects two nodes of type "PERSONA" and determines their familial relationship, has the following properties:
  - "Relacio" (relationship): Indicates the type of relationship between the two nodes (son, daughter, spouse, etc.)
  - "Relacio_Harmonitzada" (harmonized relationship): The same as "Relacio" but always in catalan. 

