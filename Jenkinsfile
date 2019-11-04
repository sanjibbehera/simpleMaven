pipeline {
  agent any
  
  stages {
    stage ('Compile Stage') {
        steps {
        def mvnHome = tool name: 'maven', type: 'maven'
            withMaven(maven: 'maven'){
              //sh 'mvn clean compile'
              sh "${mvnHome}/bin/mvn clean compile"
            }
        }
    }
    
    stage ('Testing Stage'){
        steps {
        def mvnHome = tool name: 'maven', type: 'maven'
            withMaven(maven: 'maven'){
              //sh 'mvn test'
              sh "${mvnHome}/bin/mvn test"
            }
        }
    }
    
    stage ('Deployment Stage'){
      steps{
        def mvnHome = tool name: 'maven', type: 'maven'
        withMaven(maven: 'maven'){
            //sh 'mvn deploy'
          sh "${mvnHome}/bin/mvn deploy"
        }
      }
    }
  }
}
