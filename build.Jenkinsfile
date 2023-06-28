pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-2.amazonaws.com
                docker build -t shambhavee-jenkins .
                docker tag shambhavee-jenkins:{$BUILD_NUMBER} 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:{$BUILD_NUMBER}
                docker push 854171615125.dkr.ecr.us-east-2.amazonaws.com/shambhavee-jenkins:{$BUILD_NUMBER}
                '''
    }
}