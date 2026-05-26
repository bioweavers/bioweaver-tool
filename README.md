<h1 align="center">

Bio Weaver Tool

</h1>

<h2 align="center">

**Dashboard for Rincon Consultants, Inc.**

<h2 align="center">

## Table of Contents

[Tool Description](#tool-description)

[Repository Structure](#repository-structure)

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
│   ├── 1_Search.py           # Dashboard page 1
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
(Describe repo structure generally here)

## Installation Instructions

### Configure the environment 
1. Download and install VS Code if needed: https://code.visualstudio.com/Download
   
2. Install Mambda if needed: https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html
   
3. Clone the repository from GitHub. In the terminal, run:
   ```
   git clone https://github.com/bioweavers/bioweaver-tool.git 
   ```
4. Create a new environment. In the terminal, run:
   ```
   mamba env create -f environment.yml
   ```
5. Activate the environment. In the terminal, run:
   ```
   mamba activate bioweavers-gdf
   ```

### Data Setup and Updates
Before running the dashboard, ensure that all required datasets are correctly placed and formatted. 

All input data must be stored in the data/ folder. 

Ensure data is updated on your local machine by creating any missing folders that have been stored in the .gitignore or adding updated data files. To ensure functions operating on these files run smoothly, please change the file names to:
```
data/
├── cnddb/          # Current CNDDB data
│   ├── cnddb.dbf
│   ├── cnddb.prj
│   ├── cnddb.shp
│   └── cnddb.shx
└── cnps.csv        # Current CNPS data
```
Only include the most recent versions of the datasets. 

### Running the Dashboard Locally
1. Navigate to the root folder.
   ```
   cd bioweaver-tool
   ```

2. In the terminal run:
   ```
   streamlit run Home.py
   ```
   Alternatively, you can manually paste http://localhost:8501 into the browser if needed.
   
3. Close the app when finished with analysis. In the terminal, run
   ```
   Ctrl C
   ```

### Running the Dashboard with Docker

1. Install Docker Desktop if needed: https://docs.docker.com/desktop/
   
2. Launch Docker Desktop
   
3. Build Docker image
  - Ensure that you are in the root folder of the dashboard app, i.e. running
    ```
    pwd
    ```
    In the terminal should return a file path ending in /bioweaver-tool
  - In the terminal, run the command to build the app:
    ```
    docker-compose up --build
    ```

4. Open the dashboard in a browser on your local machine:
     http://localhost:3009
   - Alternatively, view the dashboard in Docker Desktop in the containers tab.
     
5. Stop the Docker container when you are done with the dashboard.
  - In the terminal press d to detach, or run
    ```
    docker-compose down
    ```
    - Alternatively, stop the container in Docker Desktop using the blue square.

## Authors and contributors 
- Jaslyn Miura {[Github](https://github.com/jaslynmiura) | [Website](https://jaslynmiura.github.io/) | [LinkedIn](https://www.linkedin.com/in/jaslyn-miura/)}

- Melannie Moreno Rolón {[Github](https://github.com/mmorenorolon) | [Website](https://mmorenorolon.github.io/) | [LinkedIn](https://www.linkedin.com/in/melanniemoreno/)}

- Ava Robillard {[Github](https://github.com/avarobillard) | [Website](https://avarobillard.github.io/) | [LinkedIn](https://www.linkedin.com/in/avarobillard/)}
