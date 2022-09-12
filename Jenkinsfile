node("ubuntu"){
  stage("Install docker"){
    sh '''
    sudo apt-get update
    sudo apt-get install docker.io -y
    sudo snap install docker 
    sudo docker version
    '''
  }
  stage("Build and push????"){
  def img = docker.build("denemeagent/deneme:${env.BUILD_ID}")
  customImage.push()
  }
}
