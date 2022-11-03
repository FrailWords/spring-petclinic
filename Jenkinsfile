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

    stage('SonarScanner') {
      steps {
        sh './mvnw sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dlicense.skip=true'
      }
    }

  }
}