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

       stage('Authenticate to GCP') {
            steps {
                sh '''
                    # Using VM's default service account
                    gcloud auth list
                    gcloud config set project ${PROJECT_ID}
                    gcloud config set compute/region ${REGION}
                '''
            }
        }
    }
}
