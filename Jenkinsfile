pipeline {
    agent none
    stages {
        stage('Example Build') {
            agent { docker 'maven:3.9.9-eclipse-temurin-21' }
            steps {
                echo 'Hello, Maven'
                sh 'mvn --version'
            }
        }
        stage('Example Test') {
            agent { docker 'openjdk:21-jre' }
            steps {
                echo 'Hello, JDK'
                sh 'java -version'
            }
        }
    }
}
