pipeline {
    agent {
        docker {
            image 'gcp-image:v1'
            args '--user=root'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test Inside Container') {
            steps {
                sh 'which git'
                sh 'git --version'
                sh 'ls -l'
            }
        }
    }
}
