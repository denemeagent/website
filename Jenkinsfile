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
        sudo rm -rf ./containerd.io_1.5.11-1_amd64.deb  
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/containerd.io_1.4.8-1_amd64.deb
        sudo dpkg -i ./containerd.io_1.4.8-1_amd64.deb
        sudo dpkg -i ./docker-ce-cli_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        sudo dpkg -i ./docker-ce-rootless-extras_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        sudo dpkg -i ./docker-ce_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        sudo dpkg -i ./docker-compose-plugin_2.3.3~ubuntu-hirsute_amd64.deb
        sudo dpkg -i ./docker-scan-plugin_0.17.0~ubuntu-hirsute_amd64.deb
        ls
        sudo docker version
        '''
      }
    }
  }
}
