pipeline {
    agent any
    tools { nodejs "NodeJS 12.16.2"}
    stages {
        stage('Install Dependencies') { 
            steps {
                echo 'INSTALLING DEP'
                RUN apt-get install libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb
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
