pipeline {
  agent {
    docker {
      image 'python:3.7.3-stretch'
    }

  }
  stages {
    stage('Requirements') {
      parallel {
        stage('Requirements') {
          steps {
            sh '''#!/bin/bash
python3 -m venv venv
. venv/bin/activate
make install
'''
          }
        }

        stage('Install Hadolint') {
          steps {
            sh '''#!/bin/bash
# Run hadolint
apt get install docker
docker run --rm -i hadolint/hadolint < Dockerfile'''
          }
        }

      }
    }

    stage('Lint') {
      steps {
        sh '''. venv/bin/activate
make lint'''
      }
    }

  }
}