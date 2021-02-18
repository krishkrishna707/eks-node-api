pipeline {
    agent any 
     environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
        REGION                = 'us-east-1'
    }      
    stages {
        stage('DOCKER IMAGE BUILD') {
            steps {
                sh '''
                    docker build -t 456774515540.dkr.ecr.us-east-1.amazonaws.com/node .
                    echo "completed"
                '''
            } 
        }
        stage('DOCKER IMAGE PUSH') {
            steps {
                sh '''
                    aws configure set region $REGION
                    aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 456774515540.dkr.ecr.us-east-1.amazonaws.com
                    docker push 456774515540.dkr.ecr.us-east-1.amazonaws.com/node
                    echo "completed"
                '''
            } 
        }
        stage('Build') {
            steps {
                sh '''
                aws sts get-caller-identity
                # kubectl apply -f kube-deployment/deployment.yml
                echo "completed"
                '''
            } 
        }

    }
}
