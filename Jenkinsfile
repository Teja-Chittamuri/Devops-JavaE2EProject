pipeline
{
    agent none
    stages{
        stage('Buid')
        {
            agent{
                docker { image 'semoss/docker-tomcat' }
            }
            steps{
                git branch:'master', url:'https://github.com/Teja-Chittamuri/HelloWolrd-DevopsE2E.git'
            }
            steps{
                sh 'mvn clean install -Dskiptests'
            }
            steps{
                 sh 'mvn test'
            }
            steps{
                 sh 'mvn checkstyle:checkstyle'
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
