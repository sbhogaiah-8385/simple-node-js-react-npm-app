pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-node-js-react-npm-app"
        CONTAINER_NAME = "simple-node-js-container"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling code from GitHub...'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }


    }

}
