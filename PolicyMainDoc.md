
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
2) Proposal for next steps to be undertaken in the extablishment and axtention of the fusion-relevant A&M data bases, development CRMs and usage inside fusion codes. 
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












New data requests should be prioritized. At present, e+W excitation, H^+(D,T) + W - CX

Those can come from different atomic/molecular data providers (ADAS, IAEA database, NIFS, NIST etc.) 

This is largely satisfied by ADAS, mainly ADF11 and ADF15 datasets
Process resoloved data is available from D.Fursa group (own database…) but it is recommended to take the data via CollisionDB. This is fundamental cross section data (including differential ones). This data may partially be already available in ADAS; if missing, but higher level data is needed the participants of this group are welcome to take the effort to put the data (after reasonbable checks) to ADAS.

Expansion of ADF15 line transitions list available for spectroscopic data comparison with codes. The fundamental data may already exist but just needs post-processing. There is some ITPA-diagnostics effort to collate desired line lists. There may be merit in curating a smaller set of files specifically for AMNS purposes.

Some dedicated effort must be made to bring the finer data at the individual rate level to the coarser description needed by many codes (effective cooling rates, total radiation emissivity, total particle balance)

For ADAS formats, and particularly those used by major fusion modelling codes, add in a metadata block (following FAIR definition) to include summary of contents, ranges, dependencies and units. This should be separate from the existing comments.


