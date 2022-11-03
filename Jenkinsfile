pipeline {
  agent any
  stages {
    stage('Package') {
      steps {
        sh '''./mvnw package
'''
        archiveArtifacts(artifacts: 'build/libs/**/*.jar', allowEmptyArchive: true)
      }
    }

  }
}