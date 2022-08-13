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
                //sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/DWA/target/customwarname.war  Cyberone@54321@52.172.252.88:/usr/local/tomcat/webapps"
                  sh  "docker cp /var/lib/jenkins/workspace/DWA/target/customwarname.war 1bd62bbb7c2e:/usr/local/tomcat/webapps"
            }   
        }
        
        
       
    }
}
