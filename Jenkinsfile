pipeline {
  agent none
  stages {
    stage('Fluffy Build') {
      agent {
        node {
          label 'jdk7-node'
        }

      }
      steps {
        sh './jenkins/build.sh'
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
        sh 'echo $name'
      }
    }

    stage('Fluffy Test') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        sh ' ./jenkins/test-all.sh'
        junit '**/surefire-reports/**/*.xml'
      }
    }

  }
  environment {
    name = 'Chakravarthy'
  }
}