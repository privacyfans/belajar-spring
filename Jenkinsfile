pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build Start'
                sh("./mvmw clean compile test-compile")
                echo 'Build Stop'
            }
        }

        stage('Test') {
            steps {
                echo 'Test 1'
                sh("./mvnw test")
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

   
