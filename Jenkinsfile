pipeline {
    agent {
        docker {
            image 'gcp-image:v1'
            args '-u root'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SanthaprakashMahendran/testing-dr.git'
            }
        }
    }
}
