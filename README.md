# E-CROSS
This repository contains the optimisation code and the origin-destination data of the publication by Eggimann and Romano (2026).

    Eggimann, S., Romano, E. (2026): Using electric vehicles for cross-border electricity transmission in borderland cities. Under review.
    DOI: tbd.

We refer to the publication for a detailed description of:
  - the modelling of the electric vehicle origin–destination matrix, and
  - the optimisation framework implemented in this repository.

## File overview
| Syntax                | Description |
| -----------           | ----------- |
| LICENSE               | Licensing  information       |
| main.py               | Main loop of the optimisation code       |
| methods.py            | Methods used in the optimisation              |
| trip_OD_matrix.csv    | Origin-destination matrix of electric vehicles between France and Switzerland  |

## System requirements
The optimisation was performed in Python (Version 3.10), using Pyomo package and 'CBC' solver. No non-standard hardware is necessary to replicate the simulations.
For large OD matrices, running the optimisation on a local machine might take several days, so using cluster computing is advised.

## Installation guide
Two steps are required to run the optimisation code.
1. To run the `main.py` and `methods.py` file, access to market data (via `get_EPEX()`) is required. In this study, market data are retrieved by the authors from their internal Filemaker database. To reproduce the analysis, users must obtain their own market data from the EEX GROUP (https://www.epexspot.com/en) and ENTSO-E Transparency Platform (https://transparency.entsoe.eu/). 

2. The information on the trips and electric vehicle traffic needs to be provided in an origin-destination `.csv` file. Here. the OD matrix of the simulation is provided (`trip_OD_matrix.csv `) that includes all information for the study, except the distances, which were calculated using the [Google API](https://developers.google.com/maps/documentation/directions).  

    | Attribute                        | Description |
    | -----------                      | ----------- |
    | `'local_admin_unit_id_from'`     | Origin ID |
    | `'local_admin_unit_id_to'`       | Destination ID |
    | `'distance'`                     | Distance between origin and destination in km and needs to be calculated (e.g. using Google API) |
    | `'nb_vehicles_adj'`              | Number of electric vehicles |

## Links to all used datasets
Different public data sources were collected and used for modelling the OD-matrix in this publication and are listed below:
- Observatoirs statistique Transfrontalier. Observatoirs statistique transfrontalier synthèse 2021. [Data link](https://www.statregio-francosuisse.net))
- Federal Statistical Office. Foreign cross-border commuters by commune of work and sex. [Data link](https://www.bfs.admin.ch/bfs/en/home.assetdetail.19484857.html).
- Federal Statistical Office. Foreign cross-border commuters living in France by canton of work, department of residence and sex. [Data link](https://www.bfs.admin.ch/bfs/en/home/statistics/work-income/employment-working-hours/economically-active-population/cross-border-commuters.assetdetail.36198654.html )
- INSEE. Déplacement domicile/travail en 2021 Recensement de la population - Base des tableaux détaillés. [Data link](https://www.insee.fr/fr/statistiques/8200836?sommaire=8205947)
Federal Statistical Office. Transport transfrontalier de personnes sur la route. [Data link](https://www.bfs.admin.ch/asset/en/25885611)
- Bundesamt für Statistik. Mobilitätsverhalten der Bevölkerung. Ergebnisse des Mikrozensus Mobilität und Verkehr 2021. (2023). [Data link](https://www.bfs.admin.ch/asset/de/24165261)



