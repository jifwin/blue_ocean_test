pipeline {
  agent any
  stages {
    stage('Sync') {
      steps {
        sh '''echo "Sync start"
sleep 5
echo "Sync finished"'''
      }
    }
    stage('Build') {
      steps {
        sh '''echo "Build start"
sleep 15
echo "Build finished"'''
      }
    }
    stage('Deploy') {
      steps {
        parallel(
          "Deploy": {
            sh '''echo "Build start"
sleep 30
echo "Build finished"'''
            
          },
          "deploy2": {
            input(message: 'deploy to prod', id: 'deploy to prod', ok: 'deploy to prod')
            
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
          "errosdfgr": {
            retry(count: 5) {
              sh 'a'
            }
            
            
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