pipeline {
    agent any
    
     parameters { string(name: 'YOLO5_IMAGE_URL', defaultValue: '', description: '') }

     environment {
        AWS_REGION_K8S = 'us-east-2'
        K8S_CLUSTER_NAME = 'k8s-batch1'
        K8S_NAMESPACE = 'shambhavee-ns'
    }
        

    stages {
        stage('Setting default namespace') {
            steps {
                    sh '''
                        aws eks --region us-east-2 update-kubeconfig --name k8s-batch1
                        sudo kubectl config set-context --current --namespace=shambhavee-ns
                    '''
            }
        }
        
        stage('Deploy') {
            steps {
                sh '''
                    cd k8s
                    sudo kubectl apply -f yolo5.yaml
                '''
            }
        }
    }
}




    
    