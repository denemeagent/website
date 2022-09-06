pipeline{
  agent {label 'ubuntu-2004'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        rm -rf containerd.io_1.4.9-1_amd64.deb
        sudo apt-get update
        sudo wget https://download.docker.com/linux/ubuntu/dists/groovy/pool/stable/amd64/containerd.io_1.4.9-1_amd64.deb
        sudo wget https://download.docker.com/linux/ubuntu/dists/groovy/pool/stable/amd64/docker-ce-cli_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo wget https://download.docker.com/linux/ubuntu/dists/groovy/pool/stable/amd64/docker-ce-rootless-extras_20.10.8~3-0~ubuntu-groovy_amd64.deb 
        sudo wget https://download.docker.com/linux/ubuntu/dists/groovy/pool/stable/amd64/docker-ce_20.10.8~3-0~ubuntu-groovy_amd64.deb
        sudo wget https://download.docker.com/linux/ubuntu/dists/groovy/pool/stable/amd64/docker-scan-plugin_0.8.0~ubuntu-groovy_amd64.deb
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
