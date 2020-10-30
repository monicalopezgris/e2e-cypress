pipeline {
    // agent any
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
                echo 'INSTALLING DEP'
                sh 'npm install'
                sh './node_modules/.bin/cypress run'
                // bat 'yarn run cy:verify'
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
  post {
    // shutdown the server running in the background
    always {
      echo 'Stopping local server'
      sh 'pkill -f http-server'
    }
  }
}
