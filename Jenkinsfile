pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        sh './jenkins/build.sh'
        archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
        sh 'echo $name'
      }
    }

    stage('Fluffy Test') {
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