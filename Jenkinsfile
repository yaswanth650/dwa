pipeline{
    agent any
   
    environment {
        PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
       stage('GetCode - GHub'){
            steps{
                git 'https://github.com/soumenmaitra/dwa.git'
            }
         }        
        stage('Build - MVN'){
            steps{
                sh 'mvn clean package'
            }
         }
         stage('tomcat deploy'){
                steps{
                echo "hello"
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
