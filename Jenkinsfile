pipeline {
    agent {label 'you'}
    stages {
        stage('my Build') {
            steps {
                sh 'docker build -t tomcat_build:${BUILD_NUMBER} .' 
            }
        }  
        stage('publish stage') {
            steps {
                sh "echo ${BUILD_NUMBER}"
                sh 'docker login -u yetish519 -p yetish@123'
                sh 'docker tag tomcat_build:${BUILD_NUMBER} yetish519/tomcat_maven:${BUILD_NUMBER}'
                sh 'docker push yetish519/tomcat_maven:${BUILD_NUMBER}'
            }
        } 
        stage( 'my deploy' ) {
        agent {label 'me'} 
            steps {
               sh 'docker pull yetish519/tomcat_maven:${BUILD_NUMBER}'
               sh 'docker rm -f mytomcat'
               sh 'docker run -d -p 8080:8080 --name mytomcat yetish519/tomcat_maven:${BUILD_NUMBER}'
            }
        }    
    } 
}
  
      
  
  
