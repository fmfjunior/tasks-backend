pipeline {
    agent any 
    tools {
        jdk 'jdk9'
        maven 'maven3'
    }
    stages {
      stage ( 'construindo' ) {
          steps {
              withMaven( 'maven3' ) {
              sh 'mvn clean package -DskipTest=true'
              }
              }
          }
      stage( 'teste unitario') {
          steps{
              withMaven( 'maven3' ) {
              sh 'mvn test' 
                    }
              }
          }
    }
}
