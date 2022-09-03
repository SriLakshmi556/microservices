pipeline {
    agent any
    environment {
    AWS_ACCOUNT_ID="399348531980"
    AWS_DEFAULT_REGION="us-east-1"
	registryCredential = "sree"
    }
   
    stages {
       
    // Deploy infra provision yaml file
    stage('Submit Stack') {
      steps{
        script {
	  sh 'aws --version'
          sh "aws cloudformation create-stack --stack-name demofatgate --template-file infrastructure/ecs.yml --region='us-east-1'"
        }
      }
    }
   
    // Deploy microservices in Fargate
    stage('Deploy to ECS Fargate') {
     steps{  
         script {
	    sh './deploy.sh us-east-1 demofargate'
         }
        }
      }   
      
    }
}
