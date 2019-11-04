pipeline {
  agent any
  
  stages {
    stage ('SCM Checkout') {
      git 'https://github.com/sanjibbehera/simpleMaven'
    }
    stage ('Compile Stage') {
        def mvnHome = tool name: 'maven', type: 'maven'
        steps {
            withMaven(maven: 'maven'){
              //sh 'mvn clean compile'
              sh "${mvnHome}/bin/mvn clean compile"
            }
        }
    }
    
    stage ('Testing Stage'){
        def mvnHome = tool name: 'maven', type: 'maven'
        steps {
            withMaven(maven: 'maven'){
              //sh 'mvn test'
              sh "${mvnHome}/bin/mvn test"
            }
        }
    }
    
    stage ('Deployment Stage'){
        def mvnHome = tool name: 'maven', type: 'maven'
      steps{
        withMaven(maven: 'maven'){
            //sh 'mvn deploy'
          sh "${mvnHome}/bin/mvn deploy"
        }
      }
    }
  }
}
