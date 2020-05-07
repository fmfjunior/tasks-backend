
pipeline {
    agent any 
    tools {
        jdk 'jdk11'
        maven 'maven3'
        
    }
    stages {
      stage ( 'construindo' ) {
          steps {
             
              sh 'mvn clean package -DskipTest=true'
              }
          }
      stage( 'teste unitario') {
          steps{
             
              sh 'mvn test' 
              }
          }
      stage( 'teste estatio scanner sonar') {
                environment {
                    scannerHome = tool 'sonar_scanner'
                }
                steps{
                    withSonarQubeEnv('sonar_scanner'){
                   
                    sh '$(sonar_scanner)/bin/sonnar-scanner -e -Dsonar.projectKey=devops -Dsonar.host.url=http://172.24.0.4:9000 -Dsonar.login=jenkins -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/mvm**,**/src/test/**,**/model/**,**Application java ' 
                    }
             }
        }
    }
}
