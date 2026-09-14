pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t trivy-demo:${BUILD_NUMBER} .'
            }
        }

        stage('Trivy Scan') {
            steps {
                sh 'trivy image --severity HIGH,CRITICAL --exit-code 0 trivy-demo:${BUILD_NUMBER}'
            }
        }

        stage('Push Image') {
            steps {
                echo 'Image is safe enough to push'
            }
        }
    }
}
