pipeline
{
    agent none
    stages{
        stage('Buid'){
         agent{
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
	    steps{
                sh 'mvn clean install -Dskiptests'
            } 

        }
    }
}
