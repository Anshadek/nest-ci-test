pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Anshadek/nest-ci-test.git'
            }
        }

        stage('Install') {
            steps {
                
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm run test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
}