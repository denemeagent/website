pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        sudo apt-get update
        sudo apt-get install docker.io -y
        sudo snap install docker -y
        sudo docker version
        '''
      }
    }
  }
}
