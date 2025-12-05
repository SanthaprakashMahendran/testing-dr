pipeline {
    agent {
        docker {
            image 'google/cloud-sdk:latest'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    environment {
        PROJECT_ID = "project-d1bd05ab-4df5-4a42-847"
        REGION     = "asia-south1"
        REPO       = "Dr_Images"
        IMAGE_NAME = "myapp"
        IMAGE_TAG  = "project-d1bd05ab-4df5-4a42-847"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/SanthaprakashMahendran/testing-dr.git'
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

        stage('Docker Build') {
            steps {
                sh '''
                    docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

        stage('Docker Tag') {
            steps {
                sh '''
                    docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${REGION}-docker.pkg.dev/${PROJECT_ID}/${REPO}/${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }

        stage('Docker Push') {
            steps {
                sh '''
                    gcloud auth configure-docker ${REGION}-docker.pkg.dev --quiet
                    docker push ${REGION}-docker.pkg.dev/${PROJECT_ID}/${REPO}/${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }
    }
}

