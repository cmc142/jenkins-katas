pipeline {
  agent any
  stages {
    stage('Parallel execution') {
      parallel {
        stage('clone down') {
          steps {
            skipDefaultCheckout(true)
          }
        }
        stage('Say Hello') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
          }
        }

      }
    }

  }
}
