pipeline {
  agent any
  triggers{
    bitbucketPush()
  }
  stages {
    stage('Build') {
      tools {
        jdk "jdk-9"
      }
      steps {
        sh 'mvn -B clean install'
      }
    }
    stage('Deploy') {
      steps {
        withMaven() {
          sh 'mvn -B deploy'
        }
      }
    }
  }
}