pipeline {
  agent any

  stages {

    stage('Git') {
      steps {
       git branch: 'main', url: 'https://github.com/praveenRajJothibasu/AngularGettingStarted.git'

      }
    }

    stage('installation') {
      steps {
        sh 'ls'
        sh 'npm i --force'
      }
    }
    stage('build') {
      steps {
        sh 'npm run build'
        sh 'ls'
      }
    }
    
    stage('port cleaning') {
      steps {
        sh 'kill -9 $(lsof -t -i:4000) || true'
      }
    }
     
     stage('Deploying') {
      steps {
          sh 'rm -rf /var/www/html/*'
          sh 'cp -R ./dist/* /var/www/html'
      }
    }
  }
}

