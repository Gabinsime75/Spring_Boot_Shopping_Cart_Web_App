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
                sh """mvn clean verify sonar:sonar \
                -Dsonar.projectKey=Spring_Boot_SC_Web_App \
                -Dsonar.host.url=http://3.89.81.183:9000 \
                -Dsonar.login=squ_151eb88a464ef662daf58fbf6df0b185dbf5381a"""
                }
            }
        }
    }
}
