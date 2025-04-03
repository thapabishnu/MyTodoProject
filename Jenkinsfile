pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "engineer442/mytodoproject-web"
        DOCKER_CREDENTIALS_ID = 'dockerhub-credentials'  // Jenkins credential ID for Docker Hub
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/thapabishnu/MyTodoProject.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', DOCKER_CREDENTIALS_ID) {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }
}
