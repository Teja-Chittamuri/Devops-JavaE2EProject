pipeline
{
    agent none
    stages{
        stage('Buid'){
         agent{
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
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

        }
    }
}
