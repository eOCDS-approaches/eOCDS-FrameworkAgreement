# eOCDS-FrameworkAgreement

## Basic logic concept of a Framework Agreement by CPB
![Basic logic concept of a Framework Agreement by CPB](https://www.lucidchart.com/publicSegments/view/b09729c6-cc4d-44ce-be4d-2afbe2e96195/image.png)
*You can also leave your comments on it [here](https://www.lucidchart.com/invitations/accept/0d4b149a-68dd-4bcb-a0f7-a16cf07308ca)*
#### Legend
Data block | Acronym | Description
:------------ | :------------- |:-------------
Exependiture Item |EI |
Funding Source |FS |
Contracting Process |CP |
Periodic Notice |PN |
Prior Information Notice |PIN |
Framework Agreement Establishment |FAE  |
Aggregated Budget | AB |
Aggregated Forecast |AF |
Prequalification |PQ |
Prequalification Criteria | PQC | 
Expression of Interest |EoI |
Selected Suppliers |SS  |
Pre-award Catalogue Request |PCR |
Pre-award Catalogue |PaC |
Mini-competition |MC |
Purchase Order |PO |
Purchase Contract |PC |

#### Actors
Actor | Acronym | Description
:------------ | :------------- | :-------------
Buyer | 
Central Purchasing Body | CPB |  
Economic Operator | EO |
Selected Supplier | SS |

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

## eOCDS Design of a Framework Agreement by CPB

![OCDS Design of a Framework Agreement](https://www.lucidchart.com/publicSegments/view/cf36724f-6828-469c-beda-c0a1c66f6f83/image.png)
*You can also leave your comments on it [here](https://www.lucidchart.com/invitations/accept/d9317dbf-431d-4941-9208-2a3f89215754)*

### OCDS parallel records used to reflect eOCDS design for FAs

#### EI-2 
`Expenditure Item` is a stream describing a group of goods, services or works that CA plans to procure over a certain period, as well as the amount available for CA (as a sum of all the `Funding Sources` identified for this `EI` as child elements) to cover the purchases of subject of this group during the specified period. 

Attribute |  Description | Covered by
:------- | :-------- | :------
`ocid` | Global unique identifier for this expenditure item | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/identifiers/)
`tender.mainProcurementCategory` | Category of the subject of this expenditure item | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/codelists/#procurement-category)
`tender.classification` | CPV classification of the subject of this expenditure item | Not covered
`buyer` | Organization in whose interests the need is declared | [OCDS 1.1.](https://standard.open-contracting.org/latest/en/schema/reference/#release)
`planning.budget.period` | The aggregated period of availability of funding sources under this expenditure item |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`planning.budget.amount` | The absolute total value of all the funding sources under this expenditure item |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`relatedProcesses` | The link to the funding sources allocated for this exepnditure item | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 

##### FS-2-1 
`Funding Source` is a stream describing a specific source of funding for procurement of goods, services or works from a parent `Expenditure Item`. It contains information on both amount and Organization providing the fund, as well as other Organizations involved in the disposal of this particular budget: payer, donor. In addition, withing this stream it is possible to reflect a current status of described fund, which makes it possible to understand whether the given budget is approved by the providing party (treasury or donor) and to what extent. The valence of the model allows to organize the relationships of the entities described on its basis with other model entities (such as tenders and contracts). Thus, there is an opportunity to display the use of this source of fundings in announced tenders or concluded contracts.

Attribute |  Description | Covered by
:------- | :-------- | :------
`ocid` | Global unique identifier for this funding source | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/identifiers/)
`planning.budget.period` | The period of availability of this funding source |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`planning.budget.amount` | The absolute value of this funding source |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`planning.budget.amountRequested` | Future steps of representing the workflow of budget approvals | [Issue #616](https://github.com/open-contracting/standard/issues/616)
`planning.budget.status` | Future steps of representing the workflow of budget approvals | [Issue #616](https://github.com/open-contracting/standard/issues/616)
`planning.budget.sourceParty` | The organization related to this funding source |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`relatedProcesses` | The link to an Expenditure Item this FS is related to | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 

#### CP-2-1-1 
`Contracting Process` is a stream describing a specific general initiation started by CA in order to satisfy related `EI` or its part. In a common case such an initiation embraces: periodic (indicative) notice, contract notice, tendering part(s), awarding and contracting. But in case of aggregated procurement through FA - on a first stage `CP` will only include:
- general definition of a subject to be procured (as a general substance of the stream) 
- overall budget of this `CP`
- related `EI` (as a related stream), 
- related `FSs` (as a related stream(s)), 
- planned quantity and allocated budget (as a separate stream - `PN`)

Attribute |  Description | Covered by
:------- | :-------- | :------
`ocid` | Global unique identifier for this Contracting Process | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/identifiers/)
`planning.budget.amount` | The overal value of the funds allocated for this contacting process |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`planning.budget.budgetBreakdown` | Detailed budget breakdown under this contracting process, covering multiple budget funding and multiple periods |[core_extension](https://github.com/open-contracting-extensions/ocds_budget_breakdown_extension/blob/master/release-schema.json)
`tender.title` | | 
`tender.description` | |
`tender.value` | |
`tender.mainProcurementCategory` | Category of the subject of this contracting process | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/codelists/#procurement-category)
`tender.classification` | CPV classification of the subject of this contracting process | Not covered
`buyer` | Organization in whose interests the need is declared | [OCDS 1.1.](https://standard.open-contracting.org/latest/en/schema/reference/#release)
`tender.contractPeriod` | The period over which the contract is estimated or required to be active | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/#tender)
`relatedProcesses` | |
`*.relationship: x_fundingSource` | Link to related FS(s) | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 
`*.relationship: x_expenditure` | Link to related EI(s) | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 
`*.relationship: planning` | Link to related PN | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 
`*.relationship: x_framework` | Where subject is included in FA - link to related FA | [OCDS 1.1](https://standard.open-contracting.org/latest/en/schema/reference/?highlight=relatedProcess#relatedprocess) 

##### PN-2-1-1-1
`Periodic notice` - is a stream announcing an intention to conduct a tender. On this stage just hi-level params of future procedure to be indicated including estimated period of start (month or quarter), indicative specification of a subject of procurement and its quantity.

Attribute |  Description | Covered by
:------- | :-------- | :------

##### MC-2-1-1-1
`Mini Competition`

Attribute |  Description | Covered by
:------- | :-------- | :------

##### PC-2-1-1-1
`Purchase Contract`

Attribute |  Description | Covered by
:------- | :-------- | :------

#### FA-1
`Framework Agreement`

Attribute |  Description | Covered by
:------- | :-------- | :------

##### PQ-1
`Pre-Qualification`

Attribute |  Description | Covered by
:------- | :-------- | :------

##### PaC-1-1
`Pre-Award Catalogue`

Attribute |  Description | Covered by
:------- | :-------- | :------
