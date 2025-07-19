
# Policy proposal on the management of atomic and molecular data for fusion modelling

2024-11-25 – 2025-07-11

[TOC]

## Preamble

This document was initiated as an outcome of the “Meeting on unified A&M data policies” in FZ Juelich (see https://indico.euro-fusion.org/event/3240/) triggered at the Decennial IAEA Technical Meeting on Atomic, Molecular and Plasma-Material Interaction Data for Fusion Science and Technology 2024 (AMPMI 2024 - https://conferences.iaea.org/event/384/) held at the University of Helsinki, Finland, with follow-up discussion supported by a dedicated IAEA TM (see https://conferences.iaea.org/e/GNAMPP-3). It reflects the views of the informal researcher group formed during those meetings, including indirect participants.
This document is a product of those discussions and joint effort approved by consensus between the main participants listed in section "Participants".


## Participants

The following researches each with long experience of working (producing, utilizing in codes and experiments, validating etc.) have jointly developed and support the following document to be addressed to ITER, EUROfusion and IAEA so as to all fusion research community:

1. Dr. Dmitriy V. Borodin, Forschungszentrum Jülich GmbH, Germany
2. Dr. Xavier Bonnin, ITER Organisation, France
3. Dr. Martin O'Mullane, University of Strathclyde, UK
4. Prof. Dmitry Fursa, Curtin University, Australia
5. Dr. David Coster, IPP-Garching, Germany
6. Prof. Dr. Ursel Fantz, Universität Augsburg, Germany
7. Dr. Dirk Wunderlich, IPP-Garching, Germany
8. Juri Romazanov, Forschungszentrum Jülich GmbH, Germany
9. Dr. Kalle Heinola, IAEA, Austria 

It should be noted, that among those researches are are the director of ADAS (https://www.adas.ac.uk/), principal developers of SOLPS-ITER [(https://www.iter.org/](https://www.iter.org/node/20687/iter-unveils-new-tool-plasma-edge-modelling-solps-iter), ERO2.0, EIRENE (https://www.eirene.de/) and YACORA (https://www.yacora.de/), representative of MCCC data production (https://www.mccc-db.org/), long-term leader of EUROfusion AMNS activity so as the IAEA A&M Data Unit Head. Thus this intitiative group (involving indirectly also further colleagues) covers by the expertise the data production, maintainence (databases) and utilisation in fusion modelling. However, this group is absolute open for further extention by any relevant expert who shares the general view and is willing to contribute.


## Purpose of this document
This initiative has brought together data users (i.e. people responsible for modelling codes or researchers interpreting diagnostics and analysing experiments) and data providers.  It aims at identifying ways of improving the management of atomic and molecular (A&M) and plasma-material interaction (PMI) data in fusion applications. The hope is that this document will trigger a broader response in the community in developing standards for data sharing.  The suggested standards are agnostic towards the codes that might use the data, data production methods and validation tools - we aim for a commonly accepted, unified approach.   
The initiative group aims at reaching concrete goals in the interest of fundamental fusion research. We are open for broader cooperation and participation and count on support from ITER, EUROfusion, and the IAEA (as this intiative is strongly supported by the A&M Data Unit).


## Executive summary

The informal initiative group, inspired by the F.A.I.R. principles, proposes for consideration:
1) A set of data management policies - “best practices”  regarding joint work on A&M data. It is based on experience of fusion-relevant datasets development. Those policies are suggested for a broader use far beyond the initiative group.
2) A proposal for next steps to be undertaken in the establishment and extension of the fusion-relevant A&M databases, development of CRMs (collisional-radiative models), and usage inside fusion codes. 
3) A procedure to assess and recommend datasets for use in fusion modelling (including validation, quality and accuracy assessment, adequate resolution, and formatting). 


## Data types addressed in this document

A&M data can vary significantly due to production methods and their intended use. For instance, the data can have critically different levels of detail: bundled or resolved by ionisation states, resolved by internal states (including generalized metastables), resolved by Rydberg, SLJ-terms, ro-vibrational states in molecular species, etc. Often, in addition to the basic fundamental data, we need to have effective data produced for particular modelling tasks (typically requiring additional assumptions and additional \[sometimes hidden\] parameters). This may lead to multiple datasets for the same species and processes, which cannot be sorted just by quality as a parameter, but need additional descriptions for proper selection in view of a given application.

Below we list the most commonly used data-types used in the fusion plasma modelling.

### Cross-section data

At the most fundamental level, one requires a collection of data for individual processes.  We also need to deal with collision cross-section types: resolved/unresolved by states of various *resolution*, total or differential. In many cases, energy-averaged collision data can be preferable to reduce the size of the extremely high resolution needed for resonance effects (e.g. R-matrix with 100,000s point per transition). It is mostly of advantage to keep datasets produced by differerent methods complementing alternatives in a view of e.g. method advantages at various energy ranges.


### Atomic data 

For many practical purposes, the data is only required at a coarser description level. This can be e.g. Maxwell-averaged rate coefficients (effective data calculated for particular transitions depending only on electron temperature (Te) or even higher level “effective rates” depending on electron density (ne) as well using a local thermodynamic equilibrium (LTE) assumption). Effective rates may also have more parameters (e.g. neutral density, initial conditions, resolution level, assumptions on bundling, ion to electron temperature ratio, etc.). Thus, such higher-level datasets may be dependend on multiple parameterers specific for the case at hand, requiring to produce them upon request as a pre-processing step before running a simulation code. This is for example the current practice with ADAS. 


### Surface data

There is a close connection between surface data and boundary conditions at the plasma-material interface, in particular for molecular data, as the surface state (temperature, roughness, crystallographic orientation, etc...) can affect the ro-vibrational state distribution of molecules emitted from that surface, as well as other internal states. A more general discussion of surface data needs to be undertaken, but is not covered in this document.  Many of the points raised here with regard to metadata and data formats are just as relevant for surface data. 

Surface data is not limited to sputtering yields, but also includes reflection, surface recombination, implantation, etc, with dependencies not only on incident particle but also on surface state and composition/history. 

-Cmt-:	Pwi/psi processes should be commented and maybe provide a draft example of JSON file from the pwiDB
We need to have the link to the PSI data in particular in a view of SDtrimSP used in EIRENE for treating H2/D2/T2 release from the wall, but also just to have it uniform.


## BEST PRACTICES with working on A&M data

All data should be properly documented, for which we recommend to use schemas and other similar technologies, rather than just describing the data with text. 

Each data file (or group of files) should contain a metadata block in an agreed format (we recommend JSON with a schema), mandatory, and containing at least:
a)	data origin (DOI, reference, etc...) and date of production 
a1) unique ID
a2) clearly indicate the licensing associated with the data
b) data type
b1)  data acquisition method (calculated, compiled, measured, etc.)
b2)  data nature type (cross-section, rate, etc.)
c)  base process (e.g. base reaction or reaction type)
d)  reference to a detailed data description document (files structure, units, etc).
e)  general description of the data (probably at least as a comment, best containing the link to detailed description).
f)  at least a general statement about the data validity range and specifying extrapolation methods
g)  at least a general statement on the data accuracy and validation 
h)  sublayered metadata for all included data (whenever possible) and optionally containing further data description, including links to previous instances of the same dataset and indicating the significance of the changes from the previous version.

In addition to the mandatory points listed above, we recomend to extend the metadata with various optional points. 
a) using the CollisionDB ontology (https://db-amdis.org/collisiondb/) to identify species, reactions (https://amdis.iaea.org/databases/processes/), etc.
b) indicating the best interpolation method for data tables


We refer to the provided examples of the JSON metadata files described in the dedicated subsection "Metadata examples" as implementation proposals.

These metadata blocks can then be leveraged with the following practices:

1)	All data users are recommended to keep the list of the data in use (and also the history of it) based on that set of recommendations. The unified assessment of the data from this group should use that information and regularly release the unified recommendation list (of course with additional checks and considerations). This could take the form of a higher-level document with overview about different available data versions for a specific question, and comments regarding quality, and contact persons, such as for instance the OPenADAS appxa documentation (see e.g. https://open.adas.ac.uk/man/appxa-11.pdf).
2)	Make data processing as automatic as possible and make the routines available (API approach is a good practice) as open source software with necessary documentation.
3)	I/O routines should be open source; they should be universally applicable to all files of that format (versioning of any format is a must).
4) Possible use the pyvalem toolbox (https://github.com/xnx/pyvalem) to standardize the conversion of the data description to the metadata blocks.
5) Establish a set of standardized inter- and extrapolation routines (open source).
6) With regard to licensing, it is preferable to use one of the well-established sets of licenses such as e.g. the creative commons CC BY-ND (Attribution-No-Derivatives) which was suggested to allow use by commercial entities (i.e. all private fusion companies). All data should be licensed and all data provided openly should remain as such. 
// Footnote: List of licenses https://creativecommons.org/share-your-work/cclicenses/
7) Motivate and assist towards proper referencing of the data:
    -	provides (if possible) a DOI that can be used to refer to the data source and a DOI for one or more publications describing the data
    -	provides a DOI that relates to the validation method of the data
    -	provides a list of references to be cited when the data is used
    -	provides references to use cases of the data with indication of success.
    -	provides references to validation cases (if available) including the validation category.
8) Following the metadata format decided above, make any necessary changes to the IMAS Data Dictionary as it relates to such matters.
9) In accordance with F.A.I.R., keep metadata open even for datasets with restricted access. Also make it available even in case when the actual data is no longer accessible.


## Next steps 

1) New data requests should be prioritized. At present, some of the identified needs include electron-impact W excitation, and H^+(D,T) + W charge exchange.
Those can come from different atomic/molecular data providers (ADAS, IAEA database, NIFS, NIST, etc.). Often the provided data takes the final form of an ADAS dataset, mainly the ADF11 and ADF15 formats.
Other process-resolved data is available from the Curtin University group (with its own database) but it is recommended to access the data via CollisionDB (IAEA). These are fundamental cross-section data (including differential ones). These data may partially be already available in ADAS; if missing, but higher level data is needed, the participants of this group welcome effort to put the data (after reasonbable checks) into ADAS.

2) Expansion of ADF15 line transitions lists available for spectroscopic data comparison with codes. The fundamental data may already exist but just needs post-processing. There is some ITPA-diagnostics effort to collate desired line lists. There may be merit in curating a smaller set of files specifically for AMNS purposes. Make the tools for producing such data open source, well documented, and commonly available.

3) Some dedicated effort must be made to bring the finer data at the individual rate level to the coarser description needed by many codes (effective cooling rates, total radiation emissivity, total particle balance, total emissivity within a diagnostic-relevant wavelength range, ...).

4) Consider providing means to document automatically the particular dataset use experience (in the codes or post-processing analysis).

5) That the IPP group lead by Ursel Fantz generate a new set of AMJUEL-like files based on the MCCC data as used by YACORA; that this file / these files be passed to Xavier Bonnin at ITER where he will rerun the hydrogen fueling scan and document any differences that might arise; these results to appear in a conference presentation and a paper.  After this the data should be made more generally available (e.g. at PLOUTOS meaning as a standard input for EIRENE, SOLPS, and other related packages). 

6) In the longer term, it should be evaluated whether the AMJUEL format is the desired format going forward, and to identify an alternative format if appropriate.

7) As part of the IMAS-ification activity within the TSVV-5 EUROfusion activity, have EIRENE and/or its ancillary programs be able to read data in using the AMNS library from IMAS. Longer term, encourage other codes to support that format.

8) The proposed initiative will requiree focused attention and effort to be realized. Thus, it would necessary for the stakeholders to provide resources and, equally important, appoint liaison officers to coordinate actions and maintain this activity in the long run.


## Additional context 

- IAEA is a neutral forum for scientific and practical discussions for all its 180 Member States. It provides platforms, such as databases, which are free of use and are publicly available. Databases follow the FAIR principle.
- IAEA databases for A+M processes (CollisionDB) and PWI processes (pwiDB) use JSON metadata which include various information, such as reaction, process categorization (3-letter codes), data type, bibliographical reference, DOI, free comment line, fit coefficients (if any), information on the time when the data was added in the database, etc.
- This draft was circulated among participants of the IAEA Data Centres Network to get feedback and consensus:
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
-  A first effort towards the standardisation of the AMNS metadata was undertaken by EUROfusion as part of the Intergated Tokamak Modelling (ITM) task force activities, and later absorbed into the IMAS framework developed at ITER. The responsible officer for this activity over the years (Dr. D. Coster, IPP-Garching, Germany) is among the authors of this proposal.


# Note on the data quality assessment

Policies formulated in this document do not directly lead to the data quality assessment. Still, they provide an opportunity to track the history of the data production and use. That may enable following the validation experience by the data used in different applications and facilitate the work of any kind of evaluation committees.
