pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/ramkumar-24/CI-CD-pipeline.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rex5656/python-todo-app:latest .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push rex5656/python-todo-app:latest'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop python-app || true
                docker rm python-app || true
                docker pull rex5656/python-todo-app:latest
                docker run -d -p 5000:5000 --name python-app rex5656/python-todo-app:latest
                '''
            }
        }

    }
}