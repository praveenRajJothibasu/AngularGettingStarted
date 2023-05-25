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
    bat '''
    for /F "tokens=5" %%P in ('netstat -ano ^| findstr :4000') do (
      tasklist /FI "PID eq %%P" | findstr "node.exe" && (
        taskkill /F /PID %%P
      )
    )
    '''
  }
}


    stage('Deploying') {
  steps {
    bat 'rmdir /s /q C:\\var\\www\\html\\*'
    bat 'xcopy /E /I .\\dist\\* C:\\var\\www\\html\\'
  }
}

  }
}
