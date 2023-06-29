pipeline {
    agent any

    stages {
        stage('ECR Authentication and Docker login') {
            steps {
                sh '''
                    aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-west-1.amazonaws.com                
                   '''
            }
        }
                stage('Build') {

            steps {

                sh '''
                cd yolo5
                docker build -t shambhavee-jenkins .
                '''
            }
        }


        stage('Push to ECR') {

            steps {

                sh '''
                 docker tag shambhavee-jenkins:$BUILD_NUMBER 854171615125.dkr.ecr.us-west-1.amazonaws.com/shambhavee-jenkins:$BUILD_NUMBER
                 docker push 854171615125.dkr.ecr.us-west-1.amazonaws.com/shambhavee-jenkins:$BUILD_NUMBER
                '''
            }
        }
    }
}