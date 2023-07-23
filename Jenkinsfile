pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/shubhamgupta0209/jenkinsmodule.git', branch: 'testbranch', credentialsId: 'c4f26140-f98b-4789-b290-3c5460fe59e4')
      }
    }

    stage('build') {
      steps {
        bat 'run.bat'
      }
    }

    stage('Test') {
      steps {
        bat 'bat \'testcases.bat\''
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying '
      }
    }

    stage('Notify') {
      steps {
        emailext(subject: 'Blue Ocean CI Build ${currentBuild.result}', body: 'The build ${currentBuild.result}. Check the console output for details.', attachLog: true)
      }
    }

  }
}