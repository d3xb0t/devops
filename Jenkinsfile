pipeline {
  agent any
  stages {
    stage('Setup') { // Install any dependencies you need to perform testing
        steps {
          script {
            sh """
            pip install -r requirements.txt
            """
          }
        }
      }

    stage('Code Quality') {
      parallel {
        stage('Code Quality') {
          steps {
            sh 'python3 -m pylint app.py'
          }
        }

        stage('security') {
          steps {
            sh 'bash grep-it.sh ./app.py'
          }
        }

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
        sh 'docker build . -t app:latest'
      }
    }

    stage('Deploy') {
      steps {
        sh 'docker run -tdi -p 5000:5000 app:latest'
      }
    }

  }
}
