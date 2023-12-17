pipeline{
    agent any;
            stage("select k8"){
            steps{
                sh 'kubectl config use-context arn:aws:eks:us-east-1:449203461473:cluster/devops17-eks-LDEwhKpH'
            }
        }
        
        stage("connect k8"){
            steps{
                sh """
                  kubectl get nodes
                  if [$? == 0]{
                    echo "sucessfully connected cluster"
                  }
                  else{ 
                  echo "unable to connect cluster"
                  exit 1
                  }
                
            }    """
        }
        stage("deploy k8 files"){
            steps{
                sh """
                cd $WORKDIR
                kubectl apply -f deploy.yaml
                """
            }
        }
        stage("validate deployment"){
            steps{
                sh """
                kubectl get po           
                if [$? = 0]
                echo "sucessfully connected cluster"
                  }
                  else{ 
                  echo "unable to connect cluster"
                  exit 1
                  }
            }    """
        }
    }
}
