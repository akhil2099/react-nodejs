pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-node-react-app"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/akhil2099/react-nodejs.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }
        stage('Run Container') {
            steps {
                script {
                    sh 'docker stop my-app || true && docker rm my-app || true'
                    sh 'docker run -d -p 80:80 --name my-app $IMAGE_NAME'
                }
            }
        }
    }
}

