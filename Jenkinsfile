pipeline {
    agent any
    tools {
        nodejs 'yarn'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install -g yarn'
                sh 'yarn install'
            }
        }
      post { 
        always { 
            junit 'jest-junit.xml'   
            }
        }
        stage('Unit tests') {
            steps {
                sh 'yarn test'
            }
        }
        stage('E2E tests') {
            steps {
                sh 'yarn build'
                sh 'yarn test:e2e'
            }
        }
        post { 
            always { 
                junit 'cypress-junit.xml'   
            }
      }
    }
}
