
# Policy proposal on the management of atomic and molecular data for fusion modelling

2024-11-25 – 2025-07-11

[TOC]

## Preamble

This document was initiated as an outcome of the “Meeting on unified A&M data policies” in FZ Juelich (see https://indico.euro-fusion.org/event/3240/) triggered at the Decennial IAEA Technical Meeting on Atomic, Molecular and Plasma-Material Interaction Data for Fusion Science and Technology 2024 (AMPMI 2024) held at the University of Helsinki, Finland, with follow-up discussion supported by a dedicated IAEA TM (see https://conferences.iaea.org/e/GNAMPP-3). It reflects the views of the informal researcher group formed during those meeting including indirect participants.
This document is a product of those discussions and joint effort approved by consensus between the main participants listed in section "Participants".

->1 Link Helsinki


## Participants

The following researches each with long experience of working (producing, utilizing in codes and experiments, validating etc.) have jointly developed and support the following document to be addressed to ITER, EUROfusion and IAEA so as to all fusion research community:

1. ...


## Purpose of this document
This initiative has brought together data users (i.e. people responsible for modelling code or researchers interpreting diagnostics and analysing experoiments) and data providers.  It aims at identifying ways of improving the management of atomic and molecular (A&M) and plasma-material interaction (PMI) data in fusion applications. The hope is that this document will trigger a broader response in the community in developing standards for data sharing.  The suggested standards are agnostic towards the codes that might use the data, data production methods and validation tools - we aim for commonly accepted, unified approach.   
The initiative group aims at reaching concreete goals in the interest of fundamental fusion research. We are open for broader cooperation and participation and count on support from ITER, EUROfusion and the IAEA (as this intiative is strongly supported by the A&M Data Unit).


## Executive summary

The informal initiative group, inspired by the F.A.I.R principles, proposes for consideration:
1)	Set of data management policies - “Best practices”  regarding the joint work on A&M data. It is based on experience of fusion-relevant datasets development. Those policieds are suggested for a broader use far beyong the intiviative group.
2) Proposal for next steps to be undertaken in the extablishment and extention of the fusion-relevant A&M data bases, development CRMs and usage inside fusion codes. 
3) A procedure to assess and recommend datasets for use in fusion modelling (including validatiion,quality and accuracy assesment, adequate resolution and formatting). 


## Data types addressed in this document

A&M data can vary significanly due to production methods and the inteded use. For instance the data can have critically different level of detail: bundled or resolved by ionisation states, resolved by internal states (including generalized metastables), resolved by Rydberg, SLJ-terms, rovibrational states in moleculaer species etc. Often in addition to the base fundamental data we need to have effective data produced for particular modelling tasks (with additional assuptions and hidden parameters). This may lead to multiple datasets for the same species and processes, which cannot be sorted just by quality as a parameter, but need additional despription for proper selection in a view of a given application.

Below we list the most commonly used datatypes used in the fusion plasma modelling.

### Cross-section data
On most fundamental level one requires a collection of data for individual processes.  We also need to deal with collision cross-section types: resolved/unresolved by states of various finess, total or differential. In many cases energy averaged collision data can be preferable to to reduce the size of the extremely high resolutions needed for resonance effects (e.g. R-matrix with 100,000s point per transition). It is mostly of advantage to keep datasets produced by diffent methods complementing alternatives in a view of e.g. method advatages at various energy ranges.


### Atomic data 

For more practical for many purposes the data is only required at a coarser description level. This can be e.g. the Maxwell averaged rate coefficients (effective data calculated for particular transitions depending only on Te as well even higher level - “effective rates” depending on ne as well due to local termodynamic equillibrium (LTE) assumption). Effective rates may also have more parameters (e.g. neutral density, initial conditions, resolution level, assumptions on bundling, Te and Ti relation etc.). So, it may dependent on multiple parameterers specific for the case at hand, which is also the current practice with ADAS - to produce such datasets on request. incl. 


### Surface data

There is a close connection between the surface data and the boundary condition for the molecular data as the surface can affect the ro-vibrational state of the molecule starting at the surface so as initial popuplation of any other internal state. The more general discussion of surface data needs to be considered, but is not covered in this document.  Many of the points with regard to metadata and data formats are just as important for surface data. 

Surface data is not limited to sputtering yields, but also includes reflection, surface recombination, implantation, etc, with dependencies not only on incident particle but also on surface state and composition/history. 

-Cmt-:	Pwi/psi processes should be commented and maybe provide a draft example of json file from the pwiDB
We need to have the link to the PSI data in particular in a view of SDtrimSP used in EIRENE for treating H2/D2/T2 release from the wall, but also just to have it uniform.


## BEST PRACTICES with working on A&M data

All data should be properly documented, for which we recommend to use schemas and other similar technologies rather than just describing the data as a text. 

Each data file (or group of files) should contain metadata block  in an agreed format (JSON with a schema) mandatory containing at least:
a)	data origin (DOI, reference etc.) and date of production 
a1) unique ID
a2) clearly indicate the licensing associated with the data
b1)  data accuasition type (calculated, compiled, measured, etc.)
b2)  data nature type (cross-section, rate, etc.)
c)  base process (e.g. base reaction or rection type)
d)  reference to a detailed data descrition document (files structure, units etc).
e)  general description of the data (probaly at least as a comment,best containing the link to detailed description).
f) at least general statement about the data validity range and specifying extrapolation methods
g) at least general statement on the data accuracy and validation 
h) sublayered metadata for all included data (whenever possible) and optionally containing further data description, including links to previous instances of the same dataset and indicate the significance of the changes from the previous version.
We refer to the provided examples of the JSON metadata files described in the dedicated subsection "Metadata examples". 

In addition to the mandatory points listerd above we recomend extend the metadata with optional points. 
a) use the CollisionDB ontology (https://db-amdis.org/collisiondb/) to identify species, reactions (https://amdis.iaea.org/databases/processes/), etc.
b) Indicate the best interpolation method for data tables




These metadata blocks can be leveraged with the following practices:

1)	All data users are recommended to keep the list of the data in use (and also the history of it) based on that list of recommendations. The unified assesment of the data from this group should use that information and regularly release the unified recommendation list (of course with additional checks and considerations).
2)	Do data processing as automatic as possible and make the routines available (API approach is a good pratice) as open source with necessary documentation.
3)	 I/O routines should be open source; they should be universally applicable to all files of that format (versioning of any format is a must).
4) Possible use the pyvalem toolbox (https://github.com/xnx/pyvalem) to standardise the conversion of the data description to the metadata blocks.
5) Establish a set of standardized inter- and exrapolation routines (open source).
6) With regard to licencing, it is preferrable to use the well-established sets of licences such as e.g. the creative commons CC BY-ND (Attribution-NoDerivatives) which  was suggested to allow use by commercial entities (i.e. all private fusion companies). All data should be licensed and all data provided openly should remain as such. 
// Footnote: List of licences https://creativecommons.org/share-your-work/cclicenses/
7) Motivate and assist to proper referencing of the data:
    -	provides (if possible) a DOI that can be used to refer to the data source and a DOI for one or more publications describing the data
    -	provides a DOI that relates to the validation method of the data
    -	provides a list of references to be cited when the data is used
    -	Provide references to use cases of the data with indication of success.
    -	Provide reference to validation cases (if available) including the validation category.

8) Following the metadata format decided above, make any necessary changes to the IMAS Data Dictionary as it relates to such matters

9) In accordance with F.A.I.R keep metadata open even for closed datasets. Make it available even in case when the actual data is no longer accessible. The same would apply to data that has restricted access.


## Next steps 

1) New data requests should be prioritized. At present, e+W excitation, H^+(D,T) + W - CX
Those can come from different atomic/molecular data providers (ADAS, IAEA database, NIFS, NIST etc.) This is largely satisfied by ADAS, mainly ADF11 and ADF15 datasets
Process resoloved data is available from D.Fursa group (own database…) but it is recommended to take the data via CollisionDB. This is fundamental cross section data (including differential ones). This data may partially be already available in ADAS; if missing, but higher level data is needed the participants of this group are welcome to take the effort to put the data (after reasonbable checks) to ADAS.

2) Expansion of ADF15 line transitions list available for spectroscopic data comparison with codes. The fundamental data may already exist but just needs post-processing. There is some ITPA-diagnostics effort to collate desired line lists. There may be merit in curating a smaller set of files specifically for AMNS purposes. Make the tools for producing such data open source, well documented and commonly available.

3) Some dedicated effort must be made to bring the finer data at the individual rate level to the coarser description needed by many codes (effective cooling rates, total radiation emissivity, total particle balance).

4) Consider providing means to document automatically the particular dataset use experience (in the codes or analisis).

5) Recommendation 1: That the IPP group lead by Ursel Fantz generate a new set of AMJUEL-like files based on the MCCC data as used by YACORA; that this file / these files be passed to Xavier Bonnin at ITER where he will rerun the hydrogen fueling scan and document any differences that might arise; these results will appear in a conference presentation and a paper.  After this the data should be made more generally available (e.g. at PLOUTOS meaning as a standard input for EIRENE, SOLPS and other related packages). 

In the longer term, it should be considered if the AMJUEL format is the desired format going forward, and to identify an alternative format if appropriate.

6) Recommendation 2. As part of the IMAS-ification activity within the TSVV-5 EUROfusion activity, have EIRENE and/or its ancillary program be able to read data in using the AMNS library from IMAS. Longer term, encourage other codes to support that format.

7) The proposed initiative will requir focus attention and effort to be realised. Thus, it would necessary for the stakeholders to provide resources and, equally important, appoint liason officers to coordinate actions and maintain this activity in the long run.


## Additional context 

- IAEA is a neutral forum for scientific and practical discussions for all its 180 Member States. It provides platforms, such as databases, which are free of use and are publicly available. Databases follow the FAIR principle.
- IAEA databases for A+M processes (CollisionDB) and pwi processes (pwiDB) use json metadata which include various information, such as reaction, process categorization (3-letter codes), data type, bibliographical reference, DOI, free comment line, fit coefficients (if any), information on the time when the data was added in the database, etc
- This draft was circulated among participants of the IAEA Data Centres Network to get the feedback and concensus:
o	ADAS (Atomic Data and Analysis Structure), UK
o	Bariloche Atomic Centre, Argentina
o	CRAAMD (China Research Association of Atomic and Molecular Data), China
o	Forschungszentrum Jülich, Germany
o	IAEA
o	Queens University Belfast, UK
o	KAERI (Korea Atomic Energy Research Institute), Korea
o	Kurchatov Institute, Russia
o	Korea Institute of Fusion Energy (KFE), Republic of Korea
o	National Institute for Fusion Science (NIFS), Japan
o	National Institute of Standards and Technology (NIST), USA

-  A first effort towards the standartisation of the AMNS metadata was undertaken by EUROfusion as part of the Intergrated Tokamak Modelling (ITM) activities, and later absorbeb into the IMAS framework developed at ITER. The responcible officer for this activity over the years (Dr. D.Coster, IPP-Garching, Germany) is among the authors of this proposal.
