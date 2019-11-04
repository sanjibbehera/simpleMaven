pipeline {
  agent any
  
  stages {
    stage ('Compile Stage') {
        steps {
            withMaven(maven: 'maven'){
              //sh 'mvn clean compile'
              sh label: '', script: 'sh \'mvn clean compile\''
            }
        }
    }
    
    stage ('Testing Stage'){
        steps {
            withMaven(maven: 'maven'){
              //sh 'mvn test'
              sh label: '', script: 'sh \'mvn test\''
            }
        }
    }
    
    stage ('Deployment Stage'){
      steps{
        withMaven(maven: 'maven'){
            //sh 'mvn deploy'
            sh label: '', script: 'sh \'mvn deploy\''
        }
      }
    }
  }
}
