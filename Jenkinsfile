pipeline{
    agent none
    stages{
        stage("Building the war artifact"){
            agent {
                docker {image 'maven:3.8.1-adoptopenjdk-11'}
            }
            steps{
                sh 'mvn clean install -Dskiptests'
            }
        }
    }
}
