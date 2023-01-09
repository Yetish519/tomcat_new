pipeline {
    agent {label 'you'}
    stages {
        stage ('My Build') { 
            steps {
              sh 'mvn package'
              sh 'pwd'
              sh 'whoami'
              sh 'scp -R /home/you/workspace/New_Pipeline/target/hello-world-war-1.0.0.war me@172.31.14.18:/opt/tomcat/webapps/'
            }
        }
        stage ('My deploy') { 
        agent {label 'me'}
            steps {
              sh 'pwd'
              sh 'whoami'
              sh 'sudo sh /opt/tomcat/bin/shutdown.sh'
              sh 'sleep 3'
              sh 'sudo sh /opt/tomcat/bin/startup.sh'
            }
        }
    }
}
  
      
  
  
