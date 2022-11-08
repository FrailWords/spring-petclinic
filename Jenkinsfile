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
        sh '''withCredentials([usernamePassword(credentialsId: \'sonar\', usernameVariable: \'USERNAME\', passwordVariable: \'PASSWORD\')]) {
    sh \'\'\'
       ./mvnw clean install -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$USERNAME -Dsonar.password=$PASSWORD -Dlicense.skip=true -Dsonar.java.binaries=target/classes/**
    \'\'\'
}
'''
        }
      }

    }
  }