pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS_ID = 'nucesops-dockerhub'
        IMAGE_TAG = '1.0'
    }
    stages {
        stage('Prepare .env') {
            steps {
                script {
                    sh 'cp .env.example .env'
                }
            }
        }    
        stage('Validate Docker-Compose') {
            steps {
                script {
                    // Running docker-compose config command within a docker-compose container
                    sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock -v "${PWD}":/work -w /work docker/compose:1.29.2 config'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def appImage = docker.build("nucesops/ca5:${env.IMAGE_TAG}")
                }
            }
        }

        stage("Push to Docker Hub") {
            steps {
                script {
                    def appImage = docker.build("nucesops/ca5:${env.IMAGE_TAG}")
                    docker.withRegistry('https://index.docker.io/v1/', env.DOCKERHUB_CREDENTIALS_ID) {
                        appImage.push("${env.IMAGE_TAG}")
                        appImage.push("latest")
                    }
                }
            }
        }
    }
}