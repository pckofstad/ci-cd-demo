# CI/CD Demo
Resources for running a CI/CD setup demo against Azure


## 1. Create a github repo where you have ownership
    To make it fast and easy, also create a readme file. This makes it easy to validate that you have initiated and cloed correctly. 

## 2. Clone down repo to your local machine
    c:\repo\ci-cd-demo

## 3. Create project to deploy
    A simple project of any kind would do. We are going to use docker to build the project. A template might make it go faster. 

![Opprette prosjekt 1](/Images/01-create-project-01.jpg)

![Opprette prosjekt 2](/Images/01-create-project-02.jpg)

![Opprette prosjekt 3](/Images/01-create-project-03.jpg)


### 4. Run and test the app locally
    If you are using the template, run the server to check that it is working. 

### 5. Add docker support to the project
    - Right click on the BlazorApp1.Server in the solution and look in the Add submenu.
    - Click: Add docker support
    - Select linux container type
    
    - Ensure docker desktop is running before testing the the docker file locally
    - Testing can be done by selecting docker in the run-dropdown-menu

![Test docker locally](/Images/02-testing-docker-01.jpg)


### 6. Commit existing code and push
    .gitignore file is not created. Run the following command in the project folder:   
```
   dotnet new gitignore
```

### 7. Create Azure docker registry
    - Create new resource group, to make it easy to do cleanup later. Call it: CI-CD-testing
    - Create a unique name for your registry. Lower caps, only letters. 
    - SKU standard is fine
    - Create registry

### 8. Configure docker registry

    - Open Container registry
    - Click on Identity
    - Set System assigned identity to On
    - Click Save
    
    - Click Azure Role Assignment
    - Click Add Role Assignment
    - Select Scope Resource Group
    - Select Subscription (your selected subscription)
    - Select Resource group: CI-CD-testing
    - Role: AcrPull
    - Click Save

    - Click Access keys
    - Enable Admin user
    - Note down username and password


### 9. Create Azure App Service for testing
    - Select the same resource group as for the docker-registry: CI-CD-testing (just to make it easy to clean-up)
    - Define a unique name for your app1
    - Select Docker container
    - Select Linux
    - Select a region close to you
    - Create a new App Service Plan
    - Change the SKU and Size (unless you want to test the existing size.)
      I will select B1
    - Click Next: Docker

    - Select Options: Single Container
    - Select Image Source: Quickstart


### 10. Configure Azure App Service
    - Open App Service
    
    - Click Deployment Center
    - Click Source: GitHub Actions
        - You might need to log in
    - Select the GitHub organisation where you have your repo
    - Select the repo that you want to deploy
    - Select the branch you want to deploy from
    
    - Select Registry Source: Azure Container Registry
    - Select Managed Identity
    - Select Identity System Assigned
    - Select your newly created Registry
    - Under Image, write: test:latest
    - Click Save at the top of the page




### X. Create a CI/CD file from a template i your GitHub

![Build file from template ](/Images/03-yaml-build-file-01.jpg)

