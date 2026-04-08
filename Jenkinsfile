pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/Bunny-Kadari/ext.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t bunnykadari/ext .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ext || true'
                sh 'docker rm ext || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name ext bunnykadari/ext'
            }
        }
    }
}
