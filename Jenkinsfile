pipeline {
    agent {
        docker {
            image 'gcp-image:v1'
            args '-u root'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh 'echo Running inside local Docker agent'
                sh 'python3 --version'
            }
        }
    }
}
