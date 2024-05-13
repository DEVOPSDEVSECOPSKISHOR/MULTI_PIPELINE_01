### Jenkins Pipeline Script Readme

This README provides an overview and explanation of the Jenkins pipeline script provided below.

#### Overview

The Jenkins pipeline script provided is designed to automate various stages of a deployment process, including fetching code from GitHub repositories, configuring properties from a `config.properties` file, and deploying to an NGINX server.

#### Script Breakdown

1. **Initialization**: 
   - `configFile`, `companyname`, and `GitUrlSecondary` are initialized.
   - A map `config` is initialized to store key-value pairs from `config.properties`.
   - `UserName` and `PassWord` are declared.

2. **Pipeline Configuration**: 
   - Defines the Jenkins pipeline with an 'agent any'.
   - Sets up parameters for selecting the company name.

3. **Stage 1: Fetching Code**: 
   - Cleans workspace.
   - Clones the main branch of a GitHub repository.

4. **Stage 2: Configuring Properties**: 
   - Dynamically sets `companyname` based on selected parameter value.
   - Defines file paths and attempts to read properties from `config.properties`.
   - Catches and handles exceptions if properties file cannot be loaded.
   - Sets `UserName` and `PassWord` from properties file based on `companyname`.

5. **Stage 3: Cleaning Git and Verifying Credentials**: 
   - Cleans the git repository.
   - Displays `UserName` and `PassWord`.

6. **Stage 4: Fetching Code from Secondary Repository**: 
   - Sets up the URL of the secondary repository based on the `companyname`.
   - Clones the main branch of the secondary repository.

7. **Stage 5: Deploying to NGINX Server**: 
   - Sets `NGINXPATH` to workspace.
   - Cleans NGINX HTML directory.
   - Moves files from the secondary repository to the NGINX HTML directory.

#### Script Usage

1. Ensure Jenkins is properly configured to execute pipeline scripts.
2. Create a pipeline job in Jenkins.
3. Copy and paste the provided script into the pipeline script section of the Jenkins job configuration.
4. Adjust any necessary parameters or configurations based on your environment.
5. Save the configuration and run the Jenkins job.

This pipeline script automates the deployment process, fetching code from GitHub repositories and deploying it to an NGINX server, configured based on properties from a `config.properties` file.
