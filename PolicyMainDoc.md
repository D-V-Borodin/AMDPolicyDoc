
# Policy proposal on the production and management of atomic and molecular data for fusion modelling.

2024-11-25 – 2025-07-11

[TOC]

## Preamble

This document was started at the “Meeting on unified A&M data policies” in FZ Juelich (see https://indico.euro-fusion.org/event/3240/) with the continuation of the discussion supported by a dedicated IAEA TM  (see https://conferences.iaea.org/e/GNAMPP-3). It reflects the views of the informal researcher group formed during those meeting including indirect participants.
This document is a product of those discussions and joint effort approved by consensus between the main participants listed in section "Pariticipants".

## Participants

The following researches each with long experience of working (producing, utilizing in codes and experiments, validating etc.) have jointly developed and support the following document to be addressed to ITER, EUROfusion and IAEA so as to all fusion research community:

1. ...


## Purpose of this document
This meeting brought together data users (i.e. people responsible for modelling codes) and data providers and aimed at identifying ways of improving the process of producing and managing atomic and molecular (A&M) and plasma-material interaction (PMI) data in fusion modelling codes.   The hope is that this document will trigger a broader response in the community in developing standards for data sharing.  The suggested standards are agnostic towards the codes that might use the data, data production and validation tools - we aim for aare aimed in commonly accepted, unified approach.   
The initiative group aims at reaching concreteconcreete goals in the interest of fundamental fusiuon research aims at reaching concrete goals in the interest of fundamental fusion research. We are open for broader cooperation and participation and count on support from ITER, EUROfusion and, in particular, the IAEA (as the initiative was triggered by the discussions at IAEA Ddecennial Mmeeting on A&M and PMSI data),
This meeting was triggered by discussions at the Decennial IAEA Technical Meeting on Atomic, Molecular and Plasma-Material Interaction Data for Fusion Science and Technology 2024 (AMPMI 2024) held at the University of Helsinki, Finland and aims at reaching concrete goals in the interest of fundamental fusion research. 


## Executive summary

The meeting has triggered a creation of informal initiative group which proposes 2 documents for consideration:
1)	Policy document - “Best practices”  regarding the joint work on A&M data to be applied at least to owun work first,  but later on (after reaching maturity by that experience) can be suggested for a broader use.
2)	Proposal for next steps to be undertaken in the interest of joint development of A&M data bases, CRMs and related entrees to the fusion codes. 
The initial draft of the documents formulated, the work should continue after the meeting. 
We aim to seek more solid support from… 
We aim at developing a procedure to assess and recommend for use in fusion modelling the datasets (including validatiion, other quality assesment, adequate resolution and format). 

## Data types addressed in this document

### Atomic data

Data with variable resolution (bundled or resolved by ionisation states, resolved by internal states (generalized metastables), resolved by Rydberg, SLJ-terms etc. states  

Rate coefficients (basic data calculated for particular transitions depending only on Te as well as higher level - “effective rates” depending on ne as well). Effective rates may also have more parameters (e.g. ne, initial conditions,resolution level, assumptions on bundling, Te and Ti relation etc.) So, it may dependent on multiple parameterers specific for the case at hand, which is also the current practice with ADAS - to produce such datasets with varios resolution by states on request.  incl. Also parameter-dependent)
This is largely satisfied by ADAS, mainly ADF11 and ADF15 datasets


Process resoloved data is available from D.Fursa group (own database…) but it is recommended to take the data via CollisionDB. This is fundamental cross section data (including differential ones). This data may partially be already available in ADAS; if missing, but higher level data is needed the participants of this group are welcome to take the effort to put the data (after reasonbable checks) to ADAS.

Expansion of ADF15 line transitions list available for spectroscopic data comparison with codes. The fundamental data may already exist but just needs post-processing. There is some ITPA-diagnostics effort to collate desired line lists. There may be merit in curating a smaller set of files specifically for AMNS purposes.

Some dedicated effort must be made to bring the finer data at the individual rate level to the coarser description needed by many codes (effective cooling rates, total radiation emissivity, total particle balance)

For ADAS formats, and particularly those used by major fusion modelling codes, add in a metadata block (following FAIR definition) to include summary of contents, ranges, dependencies and units. This should be separate from the existing comments.

### Cross-section data
Requires collection of data from different atomic/molecular data providers (ADAS, IAEA database, NIFS, NIST etc.)
Collision cross-section types: state resolved/unresolved, total and differential. 
Energy averaged collision data as a preferred format to reduce the size of the extremely high resolutions needed for resonance effects (eg R-matrix with 100,000s point per transition).
New data requests should be prioritized. At present, e+W excitation, H^+(D,T) + W - CX






