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
    }
}
