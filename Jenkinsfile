pipeline {
    agent any
    tools {
      maven 'maven3'
      java 'jdk17'
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
                  sh '''$SCANNER_HOME/bin/sonar-scanner\ 
                  -Dsonar.projectKey=Spring_Boot_SC_Web_App\
                  -Dsonar.java.binaries=. 
                  -Dsonar.host.url=http://44.203.226.117:9000 \
                  -Dsonar.login=squ_f41f23d4e15c339fcfd02c3176611ffc600b8aa6 '''
                }
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
