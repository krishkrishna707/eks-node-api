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
                    echo "completed"
                '''
            } 
        }
        stage('DOCKER IMAGE PUSH') {
            steps {
                sh '''
<<<<<<< HEAD
                    aws configure set region $REGION
=======
                    aws configure set region us-east-1
>>>>>>> 444c1aed115dee3d58bf55ab234e371870ca272e
                    # $(aws ecr get-login --region $REGION --no-include-email)
                    docker push  jjino/node-api-server
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
<<<<<<< HEAD

=======
>>>>>>> 444c1aed115dee3d58bf55ab234e371870ca272e
