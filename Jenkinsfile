pipeline {
  agent { label 'master' }
  environment {
        DEPLOY_TO = 'master'
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '3'))
  }
  //triggers {
    //cron('@daily')
  //}
  stages {
    stage('Checkout') {
      steps {
        git branch: 'master',
        credentialsId: '8cd52665-32ef-4dd3-b919-71f1dab02d84',
        url: 'git@github.com:paulcosma/protractor-demo.git'

      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t paulcosma/protractor-demo-app .'
      }
    }
    stage('Publish') {
      when {
        // branch 'master'
        environment name: 'DEPLOY_TO', value: 'master'
      }
      steps {
        withDockerRegistry([ credentialsId: "052cba25-f00d-4ff2-b593-4e143b90515a", url: "" ]) {
          sh 'docker push paulcosma/protractor-demo-app:latest'
        }
      }
    }
    stage('Start App') {
      steps {
        sh 'docker stop protractor-demo-app || true && docker rm protractor-demo-app || true'
        sh 'docker run -d --restart always --name protractor-demo-app -p 49160:3456 paulcosma/protractor-demo-app'
      }
    }
  }
}
