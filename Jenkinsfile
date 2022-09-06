pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        rm -rf containerd.io_1.4.8-1_amd64.deb
        rm -rf docker-ce-cli_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        rm -rf docker-ce-rootless-extras_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        rm -rf docker-ce_20.10.14~3-0~ubuntu-hirsute_amd64.deb
        rm -rf docker-compose-plugin_2.3.3~ubuntu-hirsute_amd64.deb
        rm -rf docker-scan-plugin_0.17.0~ubuntu-hirsute_amd64.deb
        sudo apt-get update
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/containerd.io_1.4.9-1_amd64.deb
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/docker-ce-cli_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/docker-ce-rootless-extras_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/docker-ce_20.10.8~3-0~ubuntu-groovy_amd64.deb
        sudo wget https://download.docker.com/linux/ubuntu/dists/hirsute/pool/stable/amd64/docker-scan-plugin_0.8.0~ubuntu-groovy_amd64.deb
        sudo dpkg -i ./containerd.io_1.4.9-1_amd64.deb
        sudo dpkg -i ./docker-ce-cli_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo dpkg -i ./docker-ce-rootless-extras_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo dpkg -i ./docker-ce_20.10.8~3-0~ubuntu-groovy_amd64.deb
        sudo dpkg -i ./docker-scan-plugin_0.8.0~ubuntu-groovy_amd64.deb
        ls
        sudo docker version
        '''
      }
    }
  }
}
