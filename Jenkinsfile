pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        sudo apt-get remove docker docker-engine docker.io
        sudo apt-get update
        sudo apt install docker.io
        sudo snap install docker
        sudo docker version
        '''
      }
    }
  }
}
