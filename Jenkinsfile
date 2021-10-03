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
        retry(count: 5) {
          timeout(time: 5, unit: 'MINUTES') {
            dir(path: 'heroes-angular')
          }

        }

      }
    }

    stage('end ') {
      steps {
        warnError(message: 'Been up 5 minutes...now exiting...', catchInterruptions: true)
      }
    }

  }
}