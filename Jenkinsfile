pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build Start'
                sleep(10)
                echo 'Build Stop'
            }
        }

        stage('Test') {
            steps {
                echo 'Test 1'
                echo 'Test 2'
                echo 'Test 3'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy 1'
                echo 'Deploy 2'
                echo 'Deploy 3'
            }
        }
    }

    post{
        always{
            echo "Always Running"
        }

        success{
            echo "Yay, success!"
        }

        failure{
            echo "Oh no, failure!"
        }

        cleanup {
            echo "Don't care success or error"
        }

    }
}

   
