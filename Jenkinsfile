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
                    docker build -t jjino/node-api-server .
                    aws configure set region us-east-1
                    $(aws ecr get-login --region $REGION --no-include-email)
                    echo "completed"
                '''
            } 
        }
        stage('DOCKER IMAGE PUSH') {
            steps {
                sh '''
                    docker push -t jjino/node-api-server
                    aws configure set region us-east-1
                    echo "completed"
                '''
            } 
        }
        stage('Build') {
            steps {
                sh '''
                aws sts get-caller-identity
                echo "completed"
                '''
            } 
        }

    }
}