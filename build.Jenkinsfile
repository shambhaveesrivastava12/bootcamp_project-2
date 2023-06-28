pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                cd yolo5
                aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-2.amazonaws.com
                docker build -t shambhavee-jenkins .
                docker tag shambhavee-jenkins:$BUILD_TAG 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:$BUILD_TAG
                docker push 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:$BUILD_TAG
                '''
            }
        }
    }
}