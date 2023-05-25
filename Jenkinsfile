pipeline {
  agent any

  stages {
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/praveenRajJothibasu/AngularGettingStarted.git'
      }
    }

    stage('Installation') {
      steps {
        bat 'npm i --force'
      }
    }

    stage('Build') {
      steps {
        bat 'npm run build'
        bat 'dir' // Use 'dir' command instead of 'ls' for Windows
      }
    }

    stage('Port Cleaning') {
      steps {
        bat 'taskkill /F /IM node.exe /T' // Kill all Node.js processes
      }
    }

    stage('Deployment') {
      steps {
        bat 'xcopy /s /y .\\dist\\* C:\\var\\www\\html' // Copy files to the destination folder
      }
    }
  }
}
