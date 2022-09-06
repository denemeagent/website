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
