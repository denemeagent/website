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
        sudo apt-get update
        sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
        sudo rm -rf /var/lib/docker
        sudo rm -rf /var/lib/containerd
        ls /etc/apt/keyrings
        sudo apt-get remove docker docker-engine docker.io containerd runc -y
        sudo apt-get update
        sudo apt-get install ca-certificates curl gnupg lsb-release -y
        sudo mkdir -p /etc/apt/keyrings 
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg -o /etc/apt/keyrings/docker.gpg 
        echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y 
        sudo docker version 
        '''
      }
    }
  }
}
