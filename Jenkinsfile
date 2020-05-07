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
                    withSonarQubeEnv('sonarclient'){
                   
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=devops -Dsonar.host.url=http://localhost:9000 -Dsonar.login=jenkins -Dsonar.java.binaries=**/target/** -Dsonar.coverage.exclusions=**/mvm**,**/src/test/**,**/model/**" 
                    }
             }
        }
    }
}
