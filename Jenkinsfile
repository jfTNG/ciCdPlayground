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
        stage('Unit tests') {
            steps {
                sh 'yarn test'
            }
            post { 
                always { 
                    junit 'reports/jest-junit.xml'   
                }
            }
        }
        stage('E2E tests') {
            steps {
                sh 'yarn build'
                sh 'yarn test:e2e'
            }
            post { 
                always { 
                    junit 'reports/cypress-junit.xml'   
                }
            }
        }
    }
}
