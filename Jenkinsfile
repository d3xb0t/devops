pipeline {
  agent any
  stages {
    stage('Preparing the environment') {
      steps {
        sh 'python3 -m pip install -r requirements.txt'
      }
    }

    stage('Code Quality') {
      steps {
        sh 'python3 -m pylint app.py'
      }
    }

    stage('Test') {
      steps {
        sh 'python3 -m pytest'
      }
    }

    stage('Build') {
      agent any
      steps {
        sh 'docker build https://github.com/d3xb0t/devops.git -t app:latest'
      }
    }

    stage('Delivery') {
      steps {
        sh 'exit 1'
      }
    }

    stage('Deploy') {
      steps {
        sh 'exit 1'
      }
    }

  }
}