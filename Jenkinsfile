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
                script {
                    docker.build("bunnykadari/ext")
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh 'docker stop ext || true'
                    sh 'docker rm ext || true'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d -p 3000:3000 --name ext bunnykadari/ext'
                }
            }
        }
    }
}pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Bunny-Kadari/ext.git'
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
