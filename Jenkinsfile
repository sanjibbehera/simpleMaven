pipeline {
  agent any
  
  environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "localhost:8181"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "sanjibrepo-example"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "nexus-credentials"
    }
  
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
    
    stage("publish to nexus") {
            steps {
              nexusArtifactUploader {
        nexusVersion('nexus3')
        protocol('http')
        nexusUrl('localhost:8081')
        groupId('sp.sd')
        version('2.4')
        repository('sanjibrepo-example')
        credentialsId('nexus-credentials')
        artifact {
            artifactId('nexus-artifact-uploader')
            type('jar')
            classifier('debug')
            file('nexus-artifact-uploader.jar')
        }
      }
            }
        }

    
  }
}
