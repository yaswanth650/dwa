pipeline{
    agent any
   
    environment {
        PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
        
        
        
        stage('SCM'){
            steps{
                git 'https://github.com/soumenmaitra/dwa.git'

            }
         }        
    
        stage('SAST') {
             steps{
                     withSonarQubeEnv('SonarQube_9.5') { 
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
