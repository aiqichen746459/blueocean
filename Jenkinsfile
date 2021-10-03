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
          bat 'npm run build --main'
          archiveArtifacts 'build/**'
        }

      }
    }

    stage('deploy/start') {
      steps {
        warnError(message: 'Been up 5 minutes...now exiting...') {
          timeout(time: 5, unit: 'MINUTES') {
            dir(path: 'heroes-angular') {
              bat 'npm run quick'
            }

          }

        }

      }
    }

  }
}