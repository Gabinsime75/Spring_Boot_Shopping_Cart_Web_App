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
                    sh """$SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.projectKey=Spring_Boot_SC_Web_App \
                    -Dsonar.projectName=Spring_Boot_SC_Web_App
                    -Dsonar.javabinaries=. \
                    """
                    }
                }
            }
        }
    }
}
