pipeline {
    agent {
        docker {
            image 'gcp-image:v1'
            args '-u root'
        }
    }

    options {
        skipDefaultCheckout()   // IMPORTANT
    }

    stages {
        stage('Checkout') {
            steps {
                sh 'git --version'
                sh 'git clone -b main https://github.com/SanthaprakashMahendran/testing-dr.git .'
            }
        }
    }
}
