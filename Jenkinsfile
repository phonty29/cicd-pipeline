pipeline {
  agent any
  stages {
    stage('git checkout') {
      steps {
        git(url: 'https://github.com/phonty29/cicd-pipeline.git', branch: 'main')
      }
    }

    stage('application build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('tests') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('docker build') {
      steps {
        sh 'docker build --platform=linux/amd64 -t cicd-pipeline .'
      }
    }

    stage('docker push') {
      steps {
        sh 'docker push cicd-pipeline'
      }
    }

  }
}