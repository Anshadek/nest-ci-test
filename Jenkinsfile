pipeline {
    agent any

    stages {

        stage('Install') {
            agent {
                docker {
                    image 'node:20'
                    args '-u root'
                }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            agent {
                docker {
                    image 'node:20'
                    args '-u root'
                }
            }
            steps {
                sh 'npm run test'
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'node:20'
                    args '-u root'
                }
            }
            steps {
                sh 'npm run build'
            }
        }
    }
}