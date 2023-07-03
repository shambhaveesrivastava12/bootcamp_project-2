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
                        kubectl config set-context --current --namespace=shambhavee-ns
                    '''
            }
        }
        
        stage('Deploy') {
            steps {
                sh '''
                    cd
                    mv kubectl kubectl_1.24
                    mv bin bin_1.24 
                    curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.23.15/2023-01-11/bin/linux/amd64/kubectl
                    chmod +x ./kubectl
                    mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
                    kubectl version
                    cd k8s
                    kubectl apply -f yolo5.yaml
                '''
            }
        }
    }
}



    
    