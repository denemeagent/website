pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Hello"){
      steps{
        sh 'pwd'
        sh 'ls'
      }
    }
    stage("Install docker"){
      steps{
        sh '''
        sudo docker version 
        '''
      }
    }
  }
}
