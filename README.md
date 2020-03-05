# eOCDS-FrameworkAgreement

## Basic logic concept of a Framework Agreement by CPB
![alt text](https://www.lucidchart.com/publicSegments/view/b09729c6-cc4d-44ce-be4d-2afbe2e96195/image.png)
*You can also leave your comments on it [here](https://www.lucidchart.com/invitations/accept/0d4b149a-68dd-4bcb-a0f7-a16cf07308ca)*
#### Legend
Data block | Description
:------------ | :-------------
Exepnditure Item (EI) | 
Funding Source (FS) | 
Contracting Process (CP) |
Periodic Notice |
Prior Information Notice |
Framework Agreement Establishment | 
Aggregated Budget | 
Aggregated Forecast |
Prequalification |
Prequalification Criteria (PQC) | 
Expression of Interest (EoI) | 
Selected Candidates | 
Pre-award Catalogue Request |
Pre-award Catalogue |
Mini-competition |
Purchase Order |
Purchase Contract |

#### Actors
Actor | Description
:------------ | :-------------
Buyer | 
Central Purchasing Body (CPB) | 
Economic Operator (EO) |
Selected Supplier (SS) |

#### Data flow
*On example of Buyer's 2 fork:*

From...............| To....................| Description
:------- | :-------- | :--------
\- |`EI-2-1` | Specific need is identified (aggregated and weighted) and described 
\- |`FS-2-1-n` | Funds are identified and described. Linkages with target `EI` are established 
`EI-2-1` | `CP-2-1-1` | Contracting Process for this `EI` or its part is initiated: contract initiation is described, specific funding sources enough to cover assumed value are allocated from those `FSs` available for this a parent `EI`
`CP-2-1-1` | `PN-2-1-1-1` | Procurement process under this `CP` initially planned: a forecast and assumed value are described, delivery deadline indicated
`CP-2-1-1` | `CPB` | Procurement establishment under this `CP` is outsourced with `CPB`
`PN-2-1-1-1` | `AF-1-1` | Procurement forecast described by this `PN` is sent to be aggregated with the forecasts of other `Buyers` who also outsourced their homogeneous procurement establishments with a same `CPB`   
`CP-2-1-1` | `AB-1-1` | A budget breakdown described by under this `CP` is sent to be aggregated with the relevant breakdowns of other `Buyers` who also outsourced their homogeneous procurement establishments with a same `CPB`
`FA-1` | `PQ-1-1` | Prequalification round is initiated under this `FA` due to select relevant (qualified) suppliers to be invited to submit their offers
`PQ-1-1` | `PQC-1-1` | A set of prequalification criteria by sepcified by `CPB` under this prequalification round
`EO-n` | `EoI-1-n` | An expression of interest submited by `EO-n` within this prequalification round
`PQ-1-1` | `SS-1-1` | Number of suppliers to be invited to submit an offer is identified under this prequalification round
`FA-1` | `PaC-1-1` | A pre-award catalogue against sepcific group of forecast to be purchased is issued by `CPB`
`PaC-1-1` | `PCR-1-1` | A pre-award catalogue request against sepcific group of forecast to be purchased is sent by `CPB` to the `selected suppliers`
`SS-n` | `PCR-1-n` | A pre-award catalogue response is received from `SS-n` against `CPBs'` `PCR`
`PaC-1-1` | `MC-2-1-1-1` | Mini-competition between those `Selected Suppliers` who responded with their `PCR` to `CPBs` `PCR` initiated by `Buyer 2` under this `CP` in order to cover parent `EI` or its part
`MC-2-1-1-1` | `PC-2-1-1-1` | Purchase Contract is concluded between `Buyer 2` and the Supplier Selected under this `MC` 

## OCDS Design of a Framework Agreement by CPB

![alt text](https://www.lucidchart.com/publicSegments/view/8b99569a-a46e-40f6-bde8-bd176774602d/image.png)
*You can also leave your comments on it [here](https://www.lucidchart.com/invitations/accept/d9317dbf-431d-4941-9208-2a3f89215754)*

