pipeline{
    agent any
    tools{
        maven 'Maven'
    }
    
    stages{
        stage('SAST') {
             steps{
                    withSonarQubeEnv('Sonar') { 
                    sh 'mvn sonar:sonar '
                     sh 'cat target/sonar/report-task.txt'
                     }
             }
        }
        
         stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
     }
}
