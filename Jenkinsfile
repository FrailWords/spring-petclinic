pipeline {
  agent any
  stages {
    stage('Package') {
      steps {
        sh '''./mvnw package
'''
        archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
      }
    }

  }
}