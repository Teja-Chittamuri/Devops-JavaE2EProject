pipeline
{
    agent none
    stages{
        stage('Buid')
        {
            agent{
                docker { image 'maven:3.8.1-adoptopenjdk-11'}
            }
            steps{
                sh 'mvn clean install -Dskiptests'
            }
        }
        stage('Deploy'){
              agent{
                docker {image 'tomcat:latest'}
              }
   
            steps{
                sh 'docker build -t helloworld:v3 .'
            }
            steps{
                sh 'docker run -d --name webapp -p 8080:8080 helloworld:v3'
                
            }

        }
    }
}
