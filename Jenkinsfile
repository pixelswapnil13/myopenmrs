pipeline{
    agent { label 'JDK11'}
    stages{
        stage ('Source Code') {
            steps{
                git branch: 'feature_declarative', url: 'https://github.com/pixelswapnil13/myopenmrs.git'
            }
        }
        stage('Build the code ans SonarQube Analysis'){
        steps{ 
            withSonarQubeEnv('SONAR_8.9'){
                sh 'mvn clean package sonar:sonar'
            }  
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


//Declarative pipeline --