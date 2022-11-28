pipeline {
  agent any
  stages {
    stage('Package') {
      steps {
        sh '''
                    ./mvnw package
                '''
        archiveArtifacts(artifacts: 'target/*.jar', allowEmptyArchive: true)
      }
    }

    stage('SonarScanner') {
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'sonar', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
          script {
            sh '''
./mvnw clean install sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$USERNAME -Dsonar.password=$PASSWORD -Dlicense.skip=true -Dsonar.java.binaries=target/classes/**
'''
          }

        }

      }
    }

    stage('Deploy') {
      steps {
        ansiblePlaybook(playbook: '/opt/conf/playbook.yml', credentialsId: 'app', disableHostKeyChecking: true)
      }
    }

  }
}