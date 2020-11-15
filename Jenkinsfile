pipeline {
  agent {
    docker {
      image 'python:3.7.3-stretch'
    }

  }
  stages {
    stage('Requirements') {
      steps {
        sh '''#!/bin/bash
pip3 install -r requirements.txt --user'''
      }
    }

    stage('Install Hadolint') {
      steps {
        sh 'wget -O /bin/hadolint https://github.com/hadolint/hadolint/releases/download/v1.16.3/hadolint-Linux-x86_64 &&            chmod +x /bin/hadolint'
      }
    }

    stage('Lint') {
      steps {
        sh '. venv/bin/make lint'
      }
    }

  }
}