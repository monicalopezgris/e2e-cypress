pipeline {
  tools { nodejs "NodeJS 12.16.2"}
  agent {
    // this image provides everything needed to run Cypress
    docker {
      image 'cypress/base:10'
    }
  }
    stages {
        stage('Install Dependencies') { 
            steps {
              sh 'npm install'
            }
        }
        stage('Build') { 
            steps {
              sh 'npm run build'
            }
        }
        stage('Test') { 
            steps {
              sh 'npm run ci:cy-run'
            }
        }
    }
}