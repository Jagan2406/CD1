pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Jagan2406/CD1.git'
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                dir('frontend') {
                    script {
                        docker.build('frontend-app')
                    }
                }
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                dir('ecommerce-backend') {
                    script {
                        docker.build('backend-app')
                    }
                }
            }
        }

        stage('Run Docker Containers') {
            steps {
                script {
                    sh 'docker stop frontend-container || true'
                    sh 'docker rm frontend-container || true'
                    sh 'docker run -d --name frontend-container -p 3000:80 frontend-app'

                    sh 'docker stop backend-container || true'
                    sh 'docker rm backend-container || true'
                    sh 'docker run -d --name backend-container -p 8080:8080 backend-app'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
