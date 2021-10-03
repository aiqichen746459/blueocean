pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        bat 'rmdir /S /Q heroes-angular'
      }
    }

    stage('build') {
      steps {
        bat 'git clone https://github.com/johnpapa/heroes-angular.git'
        dir(path: 'heroes-angular') {
          bat 'npm install'
          bat 'npm run build'
        }

      }
    }

    stage('deploy/start') {
      steps {
        catchError(stageResult: 'success', message: 'Been up 5 minutes...now Been up 5 minutes...now Been up 5 minutes...now exiting...') {
          timeout(time: 2, unit: 'MINUTES') {
            dir(path: 'heroes-angular') {
              bat 'npm run quick'
            }

          }

        }

      }
    }

  }
}