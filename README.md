# Jenkins Pipeline for Java based application using Maven, SonarQube, Argo CD, Helm and Kubernetes

<img width="1321" height="659" alt="image" src="https://github.com/user-attachments/assets/c7a9fe89-db1c-4553-9f0a-37f465d638b0" />


Here are the step-by-step details to set up an end-to-end Jenkins pipeline for a Java application using SonarQube, Argo CD, Kubernetes controller, and Kubernetes:

Prerequisites:

   -  Java application code hosted on a Git repository
   -  Jenkins server
   -  Kubernetes cluster
   -  Kubernetes Operator
   -  Argo CD

Steps:

    1. Install the necessary Jenkins plugins:
       1.1 Sonarqube plugin for jenkins

    2. Create a new Jenkins pipeline:
       2.1 In Jenkins, create a new pipeline job and configure it with the Git repository URL for the Java application.
       2.2 Add a Jenkinsfile to the Git repository to define the pipeline stages.

    3. Define the pipeline stages:
        Stage 1: Checkout the source code from Git.
        Stage 2: Build the Java application using Maven.
        Stage 3: Run SonarQube analysis to check the code quality.
        Stage 4: Package the application into a JAR file.
        Stage 5: Deploy the application to a test environment using Kubernetes operator.
        Stage 6: Login into docker, build and push the image to dockerhub
        Stage 7: Login to git update deployment image lable to image label deployed to dockerhub
        Stage 8: Promote the application to a production environment using Argo CD.

    4. Configure Jenkins pipeline stages:
        Stage 1: Use the Git plugin to check out the source code from the Git repository.
        Stage 2: Use the Mave to build the Java application.
        Stage 3: Use the SonarQube plugin to analyze the code quality of the Java application.
        Stage 4: Use the Maven to package the application into a JAR file.
        Stage 5: Use Docker to build and deploy the image to dockerhub
        Stage 6: Use Argo CD to promote the application to a production environment.

    5. Set up Argo CD:
        Install Argo CD on the Kubernetes cluster.
        Set up a Git repository for Argo CD to track the changes in the Kubernetes manifests.
        

    6. Configure Jenkins pipeline to integrate with Argo CD:
       6.1 Add the Argo CD API token to Jenkins credentials.
       6.2 Update the Jenkins pipeline to include the Argo CD deployment stage.

    7. Run the Jenkins pipeline:
       7.1 Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
       7.2 Monitor the pipeline stages and fix any issues that arise.

This end-to-end Jenkins pipeline will automate the entire CI/CD process for a Java application, from code checkout to production deployment, using popular tools like SonarQube, Argo CD, Kubernetes operatoor, and Kubernetes.
