pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Bunny-Kadari/ext.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("devops-app")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d -p 3000:3000 devops-app'
                }
            }
        }
    }
}
