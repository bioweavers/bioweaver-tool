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

[Brief User Manual](#brief-user-manual)

[Authors and contributors](#authors-and-contributors)

## Tool Description

The Bio Weaver tool consists of an automated data processing workflow that is integrated with a dynamic platform, where biologists can interact with project-specific data in the form of maps, charts, and tables that can then be exported for their regulatory reporting needs. 

## Repository Structure
```
.
├── data/
│   ├── cnddb/                # Replace with current CNDDB data folder as needed
│   ├── cnps.csv              # Replace with current CNPS data as needed
│   └── california_state...   # California USGS quads
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
├── docker-compose.yml        # Files to create Docker container
├── Dockerfile
├── environment.yml           # Python environment
├── Home.py                   # Dashboard Home page
└── README.md              

```
The `data` folder contains the CNDDB and CNPS data, as well as the California statewide index of USGS quads. The `images` folder contains the Rincon and Bio Weaver tool logos. The `pages` folder contains the streamlit pages in order of appearance on the application, with `Home.py` remaining outside of this folder to act and the Home page of the application. The `src` folder contains all python scripts labeled by purpose. The `tests` folder contains all testing material used throughout the project. The `docker-compose` and `Dockerfile` are required for deployment of the application on Docker Desktop. 


## Installation Instructions

### Development Environment Setup (One-Time Setup)
1. Download and install VS Code (optional but recommended): [Download VS Code](https://code.visualstudio.com/Download)
   
2. Install Mambda: [Mamba Installation- documentation](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html)
   
3. Clone the repository from GitHub. In the terminal, run:
   ```
   git clone https://github.com/bioweavers/bioweaver-tool.git
   cd bioweaver-tool
   ```
4. Create a new environment. In the terminal, run:
   ```
   mamba env create -f environment.yml
   ```
5. Activate the environment. In the terminal, run:
   ```
   mamba activate bioweaver-env
   ```

### Running the Application Locally
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
- Important: Do not run multiple instances of the app at the same time. If you see a “port already in use error”, stop any running Streamlit processes.

### Installing Docker

To set up Docker, first install Docker Desktop for your operating system:
https://docs.docker.com/desktop/

If the operating system is a Windows computer, make sure to have the latest version of Windows Subsystem for Linux (WSL) installed. First, check that what the existing version of WSL is in the operating computer by running the following in the terminal:
```
wsl --version
```
If WSL is not installed or requires an update, run: 
```
wsl --install
wsl --update
```

Once Docker Desktop has been installed, verify the installation by running:
 `docker --version`

### Running the Application with Docker
1. Prerequisites: Docker Desktop is installed and running
   
2. First-time setup: 
Open a terminal and navigate to the project root directory. Confirm you’re in the right place by running this command:
   ```
   pwd
   ```
	The file path returned should end in /bioweaver-tool

   In the terminal, run the command to build and start the container:
   ```
   docker-compose up --build
   ```

3. Opening the application: Open the application in a browser on your local machine through the terminal: http://localhost:3009

- Alternatively, in Docker Desktop, go to the Containers tab, find `bioweaver-tool`, and click the play button. Then click on the local URL: http://localhost:3009

4. Stopping the app: Stop the Docker container when you are done with the application. In Docker Desktop, click the square stop button next to the `bioweaver-tool`. 

Within Docker Desktop, the `bioweaver-tool` container can be stopped and restarted as desired throughout the use of the tool- this is the easiest startup method after the application container is first built.


### Data Setup and Updates
Before running the application, ensure that all required datasets are correctly placed and formatted.

#### Data Directory
All input data must be stored in the data/ folder.
data/ folder
Include only the updated files in this folder. 

```
data/
├── cnddb/          # Current CNDDB data
│   ├── cnddb.dbf
│   ├── cnddb.prj
│   ├── cnddb.shp
│   └── cnddb.shx
└── cnps.csv        # Current CNPS data
```
#### Data Requirements
- Only include the most recent versions of datasets
- Do not rename files unless instructed
- Ensure files follow expected naming conventions

### Updates to Codebase
Before making any changes to the Bio Weaver Tool codebase:
1. Run the following terminal command to stop and remove the current container:
   ```
	docker-compose down
   ```
2. After making changes to the codebase, rebuild the container so that the Bio Weaver Tool reflects any updates.
   a) Repeat steps 1-4 of Running the Application with Docker to rebuild a new container that reflects all updates to the codebase, such as updating the CNPS and CNDDB databases.

## Brief User Manual
### Step 0: Navigate through the Home Page
- Read through the introduction of the Bio Weaver tool
- Click the “Start Your Analysis” button

### Step 1: Upload Project Boundary
- Upload a project boundary file (GeoJSON format)
- The boundary defines the spatial extent of the analysis

### Step 2: Select the Search Radius
Choose one of the following:
- 2-mile
- 5-mile (default)
- 10-mile
- 9-quad
This step determines how far beyond the project boundary the tool will search for species occurrences.

### Step 3: Explore Results Page
- Click the Go to Next Page button
- The application runs the analysis on the backend
- Results are returned and displayed in the application

### Application Outputs
After running a query, the application displays results across several components:
#### Map Display
  - Displays the project boundary and search radius
  - Shows species occurrence points and/or polygons
  - Allows users to visually assess spatial distribution
  - Allows users to hover over each species to see individual attributes

#### Summary Visualizations 
   - Provide quick insight into returned data- total number of occurences per species
 
#### Raw Attribute Tables
  - Contains detailed occurrence records returned from the query for each database (CNDDB and CNPS, respectively)
  - Includes species names, attributes, and spatial relationships (e.g., distance from project)
  - Can be renamed and exported in CSV format

#### Formatted PTO Table
- Potential to occur- editable with a drop-down menu
- Habitat Suitability and observation notes- freely editable 
- Select ‘Save Edits' to save results and repopulate the PTO assigned species count
- Click 'Export to Word' to export as a Word Document
- Designed for direct use in environmental reports

Please refer to the full technical documentation for more in-depth information about the Bio Weaver tool useage and design.

## Authors and contributors 
- Jaslyn Miura {[Github](https://github.com/jaslynmiura) | [Website](https://jaslynmiura.github.io/) | [LinkedIn](https://www.linkedin.com/in/jaslyn-miura/)}

- Melannie Moreno Rolón {[Github](https://github.com/mmorenorolon) | [Website](https://mmorenorolon.github.io/) | [LinkedIn](https://www.linkedin.com/in/melanniemoreno/)}

- Ava Robillard {[Github](https://github.com/avarobillard) | [Website](https://avarobillard.github.io/) | [LinkedIn](https://www.linkedin.com/in/avarobillard/)}
