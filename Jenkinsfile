pipeline {
  agent any
  
  stages {
    stage ('Compile Stage') {
      environment {
        mvnHome = tool name: 'maven', type: 'maven'
      }
      steps {
            withMaven(maven: 'maven'){
              sh "${mvnHome}/bin/mvn clean compile"
            }
        }
              //sh 'mvn clean compile'
    }
    
    stage ('Testing Stage'){
      environment {
        mvnHome = tool name: 'maven', type: 'maven'
      }
        steps {
            withMaven(maven: 'maven'){
              //sh 'mvn test'
              sh "${mvnHome}/bin/mvn test"
            }
        }
    }
    stage ('Deployment Stage'){
      environment {
        mvnHome = tool name: 'maven', type: 'maven'
      }
      steps{
        withMaven(maven: 'maven'){
            sh 'mvn deploy'
            //sh 'mvn deploy'
          sh "${mvnHome}/bin/mvn deploy"
        }
      }
    }
    
  }
}
