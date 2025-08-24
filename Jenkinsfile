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
      sh " mvn clean pacakge"
      }
    }
   stage("deploy to tomcat") {
    steps{
     sshagent([remote-server]) {
       sh '''
       WAR_FILE=target/mywebapp.war
       REMOTE_PATH=/usr/share/tomcat/webapps
       scp -o StrictHostKeyChecking=no $WAR_FILE root@13.235.134.192:$REMOTE_PATH/
       ssh root@13.235.134.192 "sudo systemctl restart tomcat"
       '''
       }
     }  
    }
   } 

  }	
       
   
