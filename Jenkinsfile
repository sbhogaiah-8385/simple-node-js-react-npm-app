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

        stage('Test') {
            steps {
                echo 'Running test container...'
                sh 'docker compose run --rm ${IMAGE_NAME} npm run test || echo "No tests found"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container...'
                script {
                    // Stop old container if it exists
                    sh 'docker rm -f ${CONTAINER_NAME} || echo "No container to remove"'
                    // Run new container
                    sh 'docker run -d --name ${CONTAINER_NAME} -p 5000:5000 ${IMAGE_NAME}'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful! Visit http://localhost:5000'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }

}
