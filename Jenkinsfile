pipeline {
    agent {
        node {
            label 'AGENT-1'        
        }
    }

    environment { 
        GREETING = 'Hello jenkins'
    }

    //BUILD
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh """
                    echo "Here I wrote shell script"
                    echo "$GREETING"
                """
            }
        }
    }
    // POST BUILD
    post { 
        always { 
            echo 'I will always say Hello again!'
        }

        failure { 
            echo 'this runs when pipeline is failed, used generally to send alerts'
        }
        success { 
            echo 'I will always say Hello when pipeline is success'
        }
    }
}