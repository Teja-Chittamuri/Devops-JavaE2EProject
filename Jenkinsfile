pipeline {
    agent any
    environment {
        ECR_REGISTRY = "735731564843.dkr.ecr.us-west-1.amazonaws.com/helloworldapp"
        ECR_REGION = "us-west-1"
        DOCKER_IMAGE = "vproapp"
    }
    stages {
	stage('Generate artifact')
   {
	  agent{
	    docker { image 'maven:3.8.1-adoptopenjdk-11'}
		}
		steps{
		  sh 'mvn clean install -Dskiptests'
        }
	} 
    stage('Build Docker image') {
        steps {
            sh "docker build -t $DOCKER_IMAGE . "
            }
        }
    stage('Login to ECR') {
            steps {
      withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awscredentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh "aws ecr get-login-password --region $ECR_REGION | docker login --username AWS --password-stdin $ECR_REGISTRY"
                }
            }
        }
    stage('Push Docker image to ECR') {
            steps {
                sh "docker tag $DOCKER_IMAGE:latest $ECR_REGISTRY/$DOCKER_IMAGE:latest"
                sh "docker push $ECR_REGISTRY/$DOCKER_IMAGE:latest"
            }
        }
    }
}

