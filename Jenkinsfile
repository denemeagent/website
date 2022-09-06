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
        sudo apt-get install ca-certificates curl gnupg lsb-release -y
        sudo mkdir -p /etc/apt/keyrings -y
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg -y
        echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null -y
        sudo apt-get update -y
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
        sudo apt-get install docker-ce="5:20.10.16~3-0~ubuntu-jammy" docker-ce-cli="5:20.10.16~3-0~ubuntu-jammy" containerd.io docker-compose-plugin -y
        docker version 
        '''
      }
    }
  }
}
