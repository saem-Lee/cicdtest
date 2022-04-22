pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dlota6746/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dltoa6746/testshop:newmainnew .
        sudo docker push brian24/testshop:newmainnew
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
	sudo kubectl set image deployment deploy-main ctn-main=dltoa6746/testshop:newmainnew
        '''
      }
    }
  }
}
