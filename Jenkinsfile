pipeline {
  agent {
    node {
      label 'heros'
    }

  }
  stages {
    stage('build') {
      steps {
        bat 'git clone https://github.com/johnpapa/heroes-angular.git'
        dir(path: 'heroes-angular') {
          bat 'npm install'
          bat 'npm run build -- --prod'
        }

        archiveArtifacts 'build/**'
      }
    }

    stage('deploy/start') {
      steps {
        retry(count: 5) {
          dir(path: 'heroes-angular')
        }

      }
    }

  }
  environment {
    build = '-p 3000:3000'
    deploy = '-p 3000:3000'
  }
}