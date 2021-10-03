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
          bat 'npm run build --prod'
          archiveArtifacts '**'
        }

      }
    }

    stage('deploy/start') {
      steps {
        retry(count: 1) {
          timeout(time: 5, unit: 'MINUTES') {
            dir(path: 'heroes-angular') {
              bat 'npm run quick'
            }

          }

        }

        catchError(message: 'Been up 5 minutes...now exiting...')
      }
    }

  }
}