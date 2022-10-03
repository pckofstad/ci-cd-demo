# CI/CD Demo
Resources for running a CI/CD setup demo against Azure


## 1. Create a github repo where you have ownership
    To make it fast and easy, also create a readme file. This makes it easy to validate that you have initiated and cloed correctly. 

## 2. Clone down repo to your local machine
    c:\repo\ci-cd-demo

## 3. Create project to deploy
    A simple project of any kind would do. We are going to use docker to build the project. A template might make it go faster. 

    ![Opprette prosjekt 1](./images/01-create-project-01.jpg)

    ![Opprette prosjekt 2](./images/01-create-project-02.jpg)

    ![Opprette prosjekt 3](./images/01-create-project-03.jpg)


### 4. Run and test the app locally
    If you are using the template, run the server to check that it is working. 

### 5. Add docker support to the project
    - Right click on the BlazorApp1.Server in the solution and look in the Add submenu.
    - Click: Add docker support
    - Select linux container type
    
    - Ensure docker desktop is running before testing the the docker file locally
    - Testing can be done by selecting docker in the run-dropdown-menu

     ![Opprette prosjekt 3](./images/02-testing-docker-01.jpg)

