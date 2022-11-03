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
        sh './mvnw clean sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sonar -Dsonar.password=sonar -Dlicense.skip=true'
      }
    }

  }
}