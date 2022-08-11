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
          
        
        stage('Tomcat deploy'){
            steps{
                echo "Deploying .."
                sh "scp /var/lib/jenkins/workspace/DWA/target/customwarname.war  Cyberone@52.172.252.88:/usr/local/tomcat/webapps"

            }   
        }
        
        
       
    }
}
