
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
                      sh 'mvn clean package sonar:sonar'                    }
             }
        }
    }
}
