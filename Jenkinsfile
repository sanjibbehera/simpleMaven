pipeline {
  agent any
  
  stages {
    stage ('Compile Stage') {
        steps {
            withMaven(maven: 'maven'){
              def mvnHome = tool name: 'maven', type: 'maven'
              //sh 'mvn clean compile'
              sh "${mvnHome}/bin/mvn clean compile"
            }
        }
    }
    
    stage ('Testing Stage'){
        steps {
            withMaven(maven: 'maven'){
              def mvnHome = tool name: 'maven', type: 'maven'
              //sh 'mvn test'
              sh "${mvnHome}/bin/mvn test"
            }
        }
    }
    
    stage ('Deployment Stage'){
      steps{
        withMaven(maven: 'maven'){
            def mvnHome = tool name: 'maven', type: 'maven'
            //sh 'mvn deploy'
          sh "${mvnHome}/bin/mvn deploy"
        }
      }
    }
  }
}
