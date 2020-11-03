pipeline {
  agent any
  tools { nodejs "NodeJS 12.16.2"}
  stages {
    stage('Install Dependencies') { 
      steps {
        echo 'INSTALLING DEP'
        bat 'yarn install'
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
}
