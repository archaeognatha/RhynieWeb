Rhynie Chert paleo-food web project 
===================================
This project, part of Tanner Frank's PhD dissertation, aims to use a comprehensive list of described fossil taxa from the Early Devonian
Rhynie and Windyfield Cherts in Scotland to reconstruct an ancient terrestrial trophic network and compare it to available webs from
modern ecosystems.

Last updated: 07-03-2025

Repo Contents:
--------------
- **RhynieGuildStructure.xlsx**: spreadsheet defining metaweb guild structure, contains two sheets:
    - Guilds: lists trophic guilds along with basic info for each (similarly structured to guilds.csv)
    - Guild composition: lists species within each guild --> this is the only place where specific taxon names are referred to in the context of the analysis structure, as all members of a guild are functionally equivalent in the code
  
- **TaxaList.xlsx**: list of published taxa from Rhynie, Windyfield and a few other Devonian sites, with relevant references used for each. Only the Rhynie and Windyfield taxa are used in the other files in this project.
  
- **RhynieTaxaNotes.docx**: Word document containing notes about the trophic habits of some of the taxa in the rhynie web

- **guilds.csv**: Lists all guilds and relevant information for analyses. this file is an input into RhynieWebCode.R and SLNcode.ipynb scripts

- **guild_matrix.csv**: adjacency matrix containing feeding relationships of all the guilds in the metaweb. this file is an input into RhynieWebCode.R and SLNcode.ipynb scripts

- **SLNcode.ipynb**: this is a julia script in a Jupyter notebook adapted from Dr. Peter Roopnarine's code from the 2024 NAPC fossil food web workshop. It takes in a guild-level metaweb (guild_matrix.csv) and species richness information (from guilds.csv) and generates a desired number of species-level networks (SLNs) that are randomized within the constraints of the metaweb structure. The script outputs two kinds of .csv files into a new directory within the directory /SLNs: " species-level adjacency matrices (matrix_X.csv), and corresponding species lists with guild assignments and basic info (speciesinfo_X.csv).

    - **SLN_maker.jl**: julia function used by SLNcode.ipynb, which constructs an empty array of appropriate size given the species richness of each guild
    - **r_no_prey.jl**: julia function used by SLNcode.ipynb, which determines the number of prey items for each species by drawing from a power law distribution

- **SLNcode.ipynb**: another julia script in a Jupyter notebook adapted from Dr. Peter Roopnarine's code from the 2024 NAPC fossil food web workshop. This one takes folders containing adjacency matrix and taxa ID files (e.g., the output from SLNcode.ipynb) and calculates summary network metrics. It outputs a summary table where each row is a different SLN replicate and each column is a different metric. The metrics it calculates are:
    - Connectance
    - mean In-degree
    - mean Net Trophic Position (NTP)
    - max NTP
    - NTP per guild (optional for input webs with defined guild structure)
    - Trophic Coherence (Johnson et al. 2014)
    - Trophic Omnivory
    - mean/characteristic Path Length
    - Modularity 
    - Loops
    - mean Centrality



- **RhynieWebCode.R**: this is an R script that takes in a food web adjacency matrix and generates relevant statistics. It is adapted from Dr. Carrie Tyler's code used in the 2024 NAPC fossil food web workshop.
