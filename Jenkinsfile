node {
    def app
    stage('Clone repository') {
      checkout scm
    }
    stage('Build image') { 
      app = docker.build('alexisdevgrp/example-app')
    }
    stage('Test'){
      app.inside {
        sh 'npm test'
      }
    }
    stage('Push Image') {
      docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push('latest')
      }
    }
}
