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
        timeout(time: 10 , unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
 // This is Build section
    stages {
        stage('Build') {
           steps {
                script{
                    sh  """

                        echo "Building"
                        echo $SUB
                        env

                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.DEPLOY}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
                     
 
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
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "prasad"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when {
                expression {"$params.DEPLOY"}
            }
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