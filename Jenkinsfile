pipeline {

    agent {
        docker {
            image 'gcp-image:v1'
            args '--entrypoint="" --user=root'
        }
    }

    environment {
        PROJECT_ID = "project-d1bd05ab-4df5-4a42-847"
        REGION     = "asia-south1"
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
                    echo "==== Active GCP Account ===="
                    gcloud auth list

                    echo "==== Setting Project ===="
                    gcloud config set project $PROJECT_ID

                    echo "==== Setting region ===="
                    gcloud config set compute/region $REGION
                '''
            }
        }

    }
}
