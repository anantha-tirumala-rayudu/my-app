pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-node-app"
    }

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning source code...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic tests...'
                sh 'node app.js & sleep 5 && curl -f http://localhost:3000 || exit 1'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    docker.image("${IMAGE_NAME}").run('-d -p 3000:3000')
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}