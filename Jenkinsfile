pipeline {
    agent any

    environment {
        REPO_URL = 'https://gitlab.com/Reece-Elder/devops-m5-nodeproject.git'
        DOCKER_IMAGE = 'my-node-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: "${REPO_URL}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${DOCKER_IMAGE}").run('-p 3000:3000')
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
