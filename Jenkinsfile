pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
         SUB = "jenkins"
    }
    options {
        timeout(time: 10 , unit: 'SECONDS')
    }

    stages {
        stage('Build') {
           steps {

                script{
                   sh  """

                     echo "Building"
                     echo $SUB
                     env
                     sleep 10
 
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
        aborted {
            echo "pipeline is aborted"
        }
    }
}