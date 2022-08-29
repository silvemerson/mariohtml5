pipeline {
  agent any
  
  environment {
        KUBECONFIG_JENKINS  = credentials('kube-master')
        IMAGE_NAME="registry:5000/supermario"
        IMAGE_TAG="0.0.${BUILD_ID}"
  }  
  stages{

    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/silvemerson/mariohtml5.git', branch: 'master'])
      }
    }    
    stage('Realizando Build'){
      steps{
        sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'

      }
    }

    stage('Realizando Push'){
      steps{
        sh 'docker push $IMAGE_NAME:$IMAGE_TAG'

      }
    }

    stage('Inicializando Kubeconfig'){
      steps{
         sh 'cat $KUBECONFIG_JENKINS > ~/.kube/config' 
      }
    }

    stage('Deploy'){
      steps{
         //sh 'kubectl apply -f manifest'
         //Ambiente foi criado, agora com o comando abaixo, só alterar o deploy
         //para a imagem que está no registry
         sh 'kubectl set image deployment/supermario-deployment *=$IMAGE_NAME:$IMAGE_TAG'
      }
    }        

  }
}
