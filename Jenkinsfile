pipeline{
  agent {label 'ubuntu'}
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
        cat ~/.docker/config.json
        echo "${TOKEN}" >> secret-text.txt
        cat ./secret-text.txt | sudo docker login --username denemeagent --password-stdin
        '''
      }
    }
    stage("Image build & push to Docker Hub"){
      steps{
        sh '''
        sudo docker image build -t denemeagent/deneme .
        sudo docker image push denemeagent/deneme:latest 
        sudo docker image ls 
        sudo docker image rm nginx denemeagent/deneme
        sudo docker image ls
        '''
      }
    }
  }
}
