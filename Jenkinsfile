pipeline {
    agent any

    stages {
        stage('Code Fetch') {
            steps {
                echo 'Fetching & clone code from GitHub repository'
                git branch: 'branch1', url: 'https://github.com/Ravij855/simple-java-maven-app.git'
            }
        }
        stage('Build Code Using Maven') {
            steps {
                echo 'Maven triggered, build going on'
                bat 'mvn clean install'
            }
        }
        stage('Testing code using surefire') {
            steps {
                echo 'Testing the code'
                bat 'mvn test'
            }
        }
        stage('Deploy .jar files'){
            steps{
                echo 'Deploy .jar files by Maven'
                bat 'mvn clean package'
            }
        }
        stage('Verify Dockerfile') {
            steps {
                echo  'Verfying the dockerfile presence'
                bat 'dir'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Build the docker image'
                bat 'docker build -t my-1st-dockerfile-project:latest .'
            }
        }
        stage('Docker Diployment and Attching Container with Ports') {
            steps {
                echo 'Using Docker Diployment and Attching to new Container Assiging  Port'
                bat 'docker run -d --name MY-DOCKER-CONTAINER01 -p 9090:8080 my-1st-dockerfile-project:latest'
            }
        }
    }
}

