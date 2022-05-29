pipeline{
    agent { label 'JDK11'}
    stages{
        stage ('Source Code') {
            steps{
                git branch: 'master', url: 'https://github.com/pixelswapnil13/openmrs-core.git'
            }
        }
        stage ('Build the code') {
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage ('Running JUNIT') {
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }
        stage ('Archive the artifacs') {
            steps{
                archiveArtifacts artifacts: '**/*.jar'
            }
        }        
    }     
}


//Declarative pipeline