pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/PES1UG21CS459-Jenkins/PES1UG21CS459_JENKINS']]])
            }
        }
        stage('Build') {
            steps {
                script {
                    // Assuming 'PES1UG21CS459-1' is the name of your Jenkins job
                    build 'PES1UG21CS459-1'
                    sh 'g++ working.cpp -o output'
                }
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }

    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
