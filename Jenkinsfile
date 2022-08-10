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
         
        stage('Trivy Image Scan') {
            steps {
                 sh 'mkdir -p reports'
                sh 'trivy image sonarqube >report.txt'
               
            }
        }
        
        
        stage('SonarQube - Docker') {
             steps{
                     withSonarQubeEnv('SonarQube_9.5') { 
                     sh "mvn sonar:sonar"
                     }
                  }
        }
        stage('Tomcat deploy'){
            steps{
                echo "hello"
            }   
         }
        
        
       
    }
}
