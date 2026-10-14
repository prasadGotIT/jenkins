pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
         SUB = "jenkins"
    }
    stages {
        stage('Build') {
           steps {

                script{
                   sh  """

                     echo "Building"
                     echo $SUB
                     env
                     
 
                   """
                }
              
              
           }
        }
        stage('Test') {
            steps {
                script{
                   sh  """

                     
                     echo "Building"
                     echo "Testing"
                   """
                }
                

            }
        }
        stage('Deploy') {
          steps {
               script{
                   sh  """

                     echo "Building"
                     echo "Deploying"
                   """
                }
            

          }
        }
    }
    post{
        always{
            echo 'I will always say Hello again'
            cleanWs()
        }
        success{
            echo 'I will run if success'
        }
        failure{
             echo 'I will run if failure'
        }
    }
}