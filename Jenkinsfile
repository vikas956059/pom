pipeline{
 agent any
  stages{
   stage("clone") {
    steps{
    git branch: 'main', credentialsId: 'github1', url: 'https://github.com/vikas956059/pom.git'
      }
     }
   stage("maven") {
     steps{
      sh " mvn clean package"
      }
    }
   stage("deploy to tomcat") {
    steps{
#     sshagent([remote-server]) {
       sh '''
#       WAR_FILE=target/mywebapp.war
#       REMOTE_PATH=/usr/share/tomcat/webapps
       scp target/mywebapp.war root@13.235.134.192:/usr/share/tomcat/webapps
       ssh root@13.235.134.192 "sudo systemctl restart tomcat"
       '''
     }  
    }
   } 

  }	
       
   
