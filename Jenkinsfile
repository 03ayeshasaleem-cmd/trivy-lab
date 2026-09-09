pipeline {
    agent any

    environment {
        DOCKER_BIN = '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe"'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat '''
                    %DOCKER_BIN% build -t trivy-demo:%BUILD_NUMBER% .
                '''
            }
        }

        stage('Trivy Scan') {
            steps {
                bat '''
                    trivy image --severity HIGH,CRITICAL --exit-code 1 trivy-demo:%BUILD_NUMBER%
                '''
            }
        }

        stage('Push Image') {
            steps {
                echo 'Image is safe enough to push'
            }
        }
    }
}
