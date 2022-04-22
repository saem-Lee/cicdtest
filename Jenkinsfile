pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/saem-Lee/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dltoa6746/testshop:newnewmain .
        sudo docker push brian24/testshop:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
	sudo kubectl set image deployment deploy-main ctn-main=dltoa6746/testshop:newnewmain
        '''
      }
    }
  }
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dlota6746/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dltoa6746/testshop:newblog .
        sudo docker push brian24/testshop:newblog
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
        sudo kubectl set image deployment deploy-main ctn-main=dltoa6746/testshop:newblog
        '''
      }
    }
  }
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dlota6746/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dltoa6746/testshop:newshop .
        sudo docker push brian24/testshop:newshop
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
        sudo kubectl set image deployment deploy-shop ctn-shop=dltoa6746/testshop:newshop
        '''
      }
    }
  }

}

