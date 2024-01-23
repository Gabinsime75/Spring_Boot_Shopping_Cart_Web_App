pipeline {
    agent any
    tools {
      maven 'maven3'
      jdk 'jdk17'
    }
   environment {
     SCANNER_HOME= tool 'sonar-scanner'
   } 

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout from SCM') {
            steps {
               git branch: 'main', url: 'https://github.com/Gabinsime75/Spring_Boot_Shopping_Cart_Web_App.git'
            }
        }
        stage('Compile') {
            steps {
                sh "mvn compile"
            }
        }
        stage('Unit Test') {
            steps {
                sh "mvn test -DskipTests=true"
            }
        }
       stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh """mvn clean verify sonar:sonar \
                    -Dsonar.projectKey=Spring_Boot_SC_Web_App \
                    -Dsonar.projectName=Spring_Boot_SC_Web_App
                    -Dsonar.host.url=http://3.89.81.183:9000 \
                    -Dsonar.login=sqp_47cfcff009ed91cc8a2077a93337ac9fa1c973c7 \
                    -Dsonar.javabinaries=. \
                    """
                    }
                }
            }
        }
    }
