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
        sh '''echo "Build start"
sleep 30
echo "Build finished"'''
      }
    }
    stage('job') {
      steps {
        build 'pipeline_job'
      }
    }
  }
}