# Introduction 
This project contains all the build components required to build and deploy iOS projects. 

# Getting Started
To get started create a new `*.yml` file and add into your project. (A sample pipeline-ci.yml is added into this repo for reference).
1. We need to create a variables group in Azure DevOps Pipeline -> Library and mention the same in variables: -> group; in pipeline.yml file.
2. In the resources: -> repositories: -> ref: the branch of Build pipeline.
3. In jobs: -> template: the relative template file needs to be mentioned.(eg. jobs-ci.yml etc)

# Variables
Breif overview of the variables used in the project.
1.    **artifactDirectory:** Name of the artifact directory used for publishing the artifacts.  
2.    **bdExclusions:** Exclusion list for Blackduck scanner. A comma-separated list of directory name patterns needs to be given. Eg: ’/dir1\/sdir/,/dir2/’ (note that slashes are required as shown).
3.    **bdProjectName:** Blackduck project name.(refer below for the project naming convention).
4.    **configuration:** Debug configuration name.
5.    **defaultScheme:** Scheme for Sonarqube analysis and building app in publish job.
6.    **destinationSimulators:** Destination Simulator for builds, Sonarqube, etc.
7.    **enableXCPretty:** Flag to enable or disable XCPretty for XcodeBuild runs
8.    **exportBuildWrapper:** If Sonarqube Build Wrapper is required then true. Required only if project is using C/C++/Objective C.
9.    **functionalTestScheme:** Functional Test Scheme.
10.    **iOSDevice:** Destination Device for builds, Sonarqube, etc.
11.    **infoPlistDirectory:** Info.plist directory path for the project.
12.    **infoPlistPath:** Path to the Info.plist file
13.    **integrationTestScheme:** Integration Test Scheme.
14.    **jazzyConfig:** Jazzy Docs configuration file location relative to the `workingDirection`.
15.    **major:** Major version no.
16.    **minor:** Minor version no.
17.    **patch:** Patch version no.
18.    **podspec:** Podspec file location relative to the `workingDirection`.
19.    **purpose:** Agent purpose name. (eg. Mobile CI)
20.    **sonarCoverageFileName:** Sonarqube coverage file name.
21.    **sonarProjectDescription:** Sonarqube project description.
22.    **sonarProjectKey:** Sonarqube project key.
23.    **sonarProjectName:** Sonarqube project name.
24.    **sonarSourceDirectory:** Sonarqube Source Directory path.
25.    **tag:** Tag format added to commits after release.
26.    **tagPattern:** Tag pattern to find the last tagged commit.
27.    **unitTestScheme:** Unit Test Scheme.
28.    **workingDirectory:** Working Directory path.
29.    **workspace:** Workspace name.
30.    **addSlather:** Boolean indicating whether a Code coverage report should be generated via Slather. Enabling this will publish the report to Azure Dashboard.
31.    **vmImage:** This is a string that represent the possible values [here] (https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/hosted?view=azure-devops&tabs=yaml).  This is a queue time variable that must be set in the UI of the pipeline.


# Parameters
1.    **enableFunctionalTesting:** Enable Functional Testing during publish job.
2.    **enableIntegrationTesting:** Enable Integration Testing & Black Duck analysis during publish job.
3.    **enableUnitTesting:** Enable Unit Testing & Sonarqube analysis during publish job.


**Note: Blackduck project naming conventions**

Format:  `<Major Function> - <Company> - <Region> - <Discipline> - <Product name>`

Where major function would be IT, EN (EN=Engineering)
Company – This is meant for Brands.  (Schlage, CISA, Interflex, Allegion, Isonas)
Options:  SLG – Schlage, CSA – Cisa, INF-Interflex, MLR-Milre, LCN, VON-VonDuprin, SVO-SimonsVoss, ISO-Isonas
Note:  Allegion is used for IT and cross-brand projects such as platforming.
Region – NA (North America), EMEIA, AP
Discipline – FW, SW
Product name

Example: for the Schlage Encode Lock, the project name would be EN-SLG-NA-FW-Encode Lock

