pipeline {
  agent any
  
  stages {
    stage ('Compile Stage') {
      environment {
        mvnHome = tool name: 'maven', type: 'maven'
      }
      steps {
            withMaven(maven: 'maven'){
              //sh 'mvn test'
              //sh "${mvnHome}/bin/mvn test"
              sh "${mvnHome}/bin/mvn clean compile"
            }
        }
              //sh 'mvn clean compile'
    }
    
    stage ('Testing Stage'){
        steps {
            withMaven(maven: 'maven'){
              sh 'mvn test'
              //sh "${mvnHome}/bin/mvn test"
            }
        }
    }
    
    stage ('Deployment Stage'){
      steps{
        withMaven(maven: 'maven'){
            sh 'mvn deploy'
        }
      }
    }
  }
}
