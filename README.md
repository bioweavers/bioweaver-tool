<h1 align="center">

Bio Weaver Tool

</h1>

<h2 align="center">

**Dashboard for Rincon Consultants, Inc.**

<h2 align="center">

## Table of Contents

[Tool Description](#tool-description)

[Repository Structure](#repository-structure)

[Data Management](#data-management)

[Installation Instructions](#installation-instructions)

[Authors and contributors](#authors-and-contributors)

## Tool Description

The Bio Weaver tool consists of an automated data processing workflow that is integrated with a dynamic platform, where biologists can interact with project-specific data in the form of maps, charts, and tables that can then be exported for their regulatory reporting needs. 

## Repository Structure
```
.
├── data/
│   ├── cnddb/                # Replace with current CNDDB data folder as needed
│   └── cnps.csv              # Replace with current CNPS data as needed
├── docs/
│   ├── PLAN.md               # Further documentation- in progress
│   └── PLAN.html
├── images/                   # Logos and other assets
├── pages/
│   ├── 1_Landing.py          # Dashboard page 1
│   ├── 2_Results.py          # Dashboard page 2
│   └── 3_Table.py            # Dashboard page 3
├── src/
│   ├── create_template.py    # Create PTO Word template         
│   ├── format_data.py        # Format data for PTO table
│   ├── geometry.py           # Spatial functions
│   ├── make_buffer.py        # Generate PTO from template
│   ├── species.py            # Species map and chart functions
│   └── pto_template.docx     # Template for PTO table
├── tests/
│   └── fixtures/
├── docker-compose.yml        # Files to create Docker container
├── Dockerfile         
├── environment.yml           # Python environment 
├── Home.py                   # Dashboard landing page
└── README.md                 

```

## Data management
CNDDB and CNPS data can be replaced within the /data folder. These files must be named exactly as shown in the repository structure in order for the functions to run properly.

## Installation Instructions


## Authors and contributors 
- Jaslyn Miura {[Github](https://github.com/jaslynmiura) | [Website](https://jaslynmiura.github.io/) | [LinkedIn](https://www.linkedin.com/in/jaslyn-miura/)}

- Melannie Moreno Rolón {[Github](https://github.com/mmorenorolon) | [Website](https://mmorenorolon.github.io/) | [LinkedIn](https://www.linkedin.com/in/melanniemoreno/)}

- Ava Robillard {[Github](https://github.com/avarobillard) | [Website](https://avarobillard.github.io/) | [LinkedIn](https://www.linkedin.com/in/avarobillard/)}
