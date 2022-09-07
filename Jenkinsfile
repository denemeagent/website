pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        sudo apt-get update
        sudo apt-get install docker.io -y
        sudo snap install docker 
        sudo docker version
        '''
      }
    }
    stage("Docker authenticate"){
      environment {
        TOKEN= credentials('docker-token')
      }
      steps{
        sh '''
        sudo docker login --username denemeagent --password "${TOKEN}"
        '''
      }
    }
    stage("Image build & push to Docker Hub"){
      steps{
        sh '''
        ls
        sudo docker image build -t denemeagent/deneme .
        sudo docker image push denemeagent/deneme:latest 
        sudo docker image ls 
        '''
      }
    }
  }
}
