pipeline {
    agent any

    stages {
        stage('Authentication and Build') {
            steps {
                sh '''
                aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-2.amazonaws.com
                '''
            }
        }
                stage('Build') {

            steps {

                sh '''
                cd yolo5
                docker build -t shambhavee-jenkins:$BUILD_TAG .
                docker tag shambhavee-jenkins:$BUILD_TAG 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:$BUILD_TAG
                '''

            }

        }


        stage('Push to ECR') {

            steps {

                sh '''
                docker push 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:$BUILD_TAG 
                '''
            }

        }
    }
}