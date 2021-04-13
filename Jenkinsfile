#!/usr/bin/env groovy

pipeline {

    agent {
        label 'docker' 
    }

    stages {
        stage('Docker node test') {
          agent {
            docker {
              // Set both label and image
              label 'docker'
              image 'node:7-alpine'
              args '--name docker-node' // list any args
            }
          }
          steps {
            // Steps run in node:7-alpine docker container on docker slave
            sh 'node --version'
          }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }
        }
    }
}
