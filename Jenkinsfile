pipeline{
  agent {label 'ubuntu'}
  stages {
    stage("Install docker"){
      steps{
        sh '''
        ls
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
        echo "${TOKEN}" > secret-text.txt
        cat ./secret-text.txt | sudo docker login --username denemeagent --password-stdin
        '''
      }
    }
    stage("Image build & push to Docker Hub"){
      steps{
        sh '''
        sudo docker image prune -f
        sudo docker image build -t denemeagent/deneme:latest .
        sudo docker images
        sudo docker image push denemeagent/deneme:latest
        '''
      }
    }
    stage("Install kubectl.."){
      steps{
        sh '''
        curl -LO "https://dl.k8s.io/release/v1.22.11/bin/linux/amd64/kubectl"
        curl -LO "https://dl.k8s.io/release/v1.22.11/bin/linux/amd64/kubectl.sha256"
        echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
        sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
        kubectl version --client
        sudo apt install -y jq
        '''
      }
    }
    stage('Deploy to GKE') {
      environment {
          PROJECT_ID = 'jenkins-af'
          CLUSTER_NAME = 'website'
          LOCATION = 'europe-west3-b'
          CREDENTIALS_ID = 'jenkins-af'
      }
      steps{
          step([
          $class: 'KubernetesEngineBuilder',
          projectId: env.PROJECT_ID,
          clusterName: env.CLUSTER_NAME,
          location: env.LOCATION,
          manifestPattern: 'deployment.yaml',
            credentialsId: env.CREDENTIALS_ID,
          verifyDeployments: true])
      }
    }
    stage('Verify the changes'){
      steps{
        sh '''
        export ip=$(kubectl get ingress -o json | jq ".items[0].status.loadBalancer.ingress[0].ip")
        echo $ip
        '''
      }
    }
  }
}
