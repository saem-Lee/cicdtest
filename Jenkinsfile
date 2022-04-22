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
        sudo docker build -t dltoa6746/testshop:index .
        sudo docker push dltoa6746/testshop:index
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl create deploy testpipeline --image=dltoa6746/testshop:index
        sudo kubectl expose deploy testpipeline --type=NodePort --port=8081 \
        --target-port=80 --name=testpipeline-svc
        '''
      }
    }
  }
}
