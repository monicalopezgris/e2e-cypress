pipeline {
    agent any
    tools { nodejs "NodeJS 12.16.2"}
    stages {
        stage('Install Dependencies') { 
            steps {
                echo 'INSTALLING DEP'
                sh 'yarn install'
                sh './node_modules/.bin/cypress run'
                // bat 'yarn run cy:verify'
            }
        }
        stage('Build') { 
            steps {
              sh 'yarn run build'
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
