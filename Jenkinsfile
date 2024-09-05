pipeline {
    agent any

    stages {
        stage('install python') {
            steps {
                sh 'apt update'
                sh 'apt install python3.10-venv -y'
            }
        }

        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest'
            }
        }
    }
}