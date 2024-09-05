pipeline {
    agent any
    tools {
        maven 'Maven398'
        jdk 'OpenJDK17'
    }

    stages {
        stage('install python') {
            steps {
                sh 'apt update'
                sh 'apt install python3.10-venv -y'
            }
        }
        stage('Fetch code') {
            steps {
                git branch: 'main', url: 'https://github.com/Dwiga/jenkins-practice.git'
            }
        }

        stage('Build') {
            steps {
                sh 'pip install -r requirements.txt'
            }

            post {
                success {
                    echo 'Now archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Test') {
            steps {
                sh 'pytest'
            }
        }
    }
}