pipeline {
    agent {
        node {
            label 'AGENT-1'        
        }
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds() //It wont allow two builds at a time
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
                    echo "Here  I wrote shell script"
                    echo "$GREETING"
                    # sleep 10            
                """
            }
        }

        stage('check params') {
            steps{
                sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"

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