pipeline{
    agent any
   
    environment {
        PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
       stage('GetCode - GH'){
            steps{
                git 'https://github.com/soumenmaitra/dwa.git'
            }
         }        
       stage('Build - MVN'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube - Docker') {
             steps{
                     withSonarQubeEnv('SonarQube_9.5') { 
                     sh "mvn sonar:sonar"
                     }
                  }
        }
       
    }
}
