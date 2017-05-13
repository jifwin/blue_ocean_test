pipeline {
  agent any
  stages {
    stage('Sync') {
      steps {
        sh '''echo "Sync start"
sleep 1
echo "Sync finished"'''
      }
    }
    stage('Build') {
      steps {
        sh '''echo "Build start"
sleep 2
echo "Build finished"'''
      }
    }
    stage('Deploy') {
      steps {
        parallel(
          "Deploy": {
            sh '''echo "Build start"
sleep 2
echo "Build finished"'''
            
          },
          "deploy2": {
            input(message: 'deploy to prod', id: 'deploy to prod', ok: 'deploy to prod')
            
          },
          "error": {
            sh 'echo "10" > revision'
            stash(name: 'stash', includes: 'revision')
            
          }
        )
      }
    }
    stage('job') {
      steps {
        parallel(
          "job": {
            build 'pipeline_job'
            
          },
          "error": {
            unstash 'stash'
            sh 'cat revision'
            
          }
        )
      }
    }
    stage('error') {
      steps {
        sleep(unit: 'MINUTES', time: 1)
      }
    }
    stage('done') {
      steps {
        echo 'done'
      }
    }
  }
}