pipeline {
    agent any
    tools { nodejs "NodeJS 12.16.2"}
    stages {
        stage('Install Dependencies') { 
            steps {
                echo 'INSTALLING DEP'
                bat 'yarn install'
                bat 'yarn run cy:verify'
            }
        }
        stage('Build') { 
            steps {
              bat 'yarn run build'
            }
        }
        stage('Test') { 
            steps {
              bat 'npm run ci:cy-run'
            }
        }
    }
  post {
    // shutdown the server running in the background
    always {
      echo 'Stopping local server'
      bat 'pkill -f http-server'
    }
  }
}