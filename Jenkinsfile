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
        sh 'docker build -t cicd-pipeline .'
      }
    }

    stage('docker push') {
      steps {
        sh '''echo $DOCKER_CREDS_PSW | docker login -u $DOCKER_CREDS_USR --password-stdin \\
docker push phonty29/cicd-pipeline'''
      }
    }

  }
  environment {
    DOCKER_CREDS = 'credentials(\'docker-hub-credentials\')'
  }
}