pipeline {
  agent any
  stages {
    stage('Parallel rund') {
      parallel {
        stage('Say Hello') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('build app & archive') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
            echo "Testübung Löschen"
            echo "List vor dem Löschen"
            sh 'ls -al'
            echo "Löschen"
            deleteDir()
            echo "List nach dem Löschen"
            sh 'ls -al'
	  }
        }

      }
    }

  }
}
