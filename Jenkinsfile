pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script{
                    for (int i = 0; i < 10; i++) {
                        echo ("Script ${i}")
                    }
                }
                echo 'Build Start'
                sh("./mvnw clean compile test-compile")
                echo 'Build Stop'
            }
        }

        stage('Test') {
            steps {
                script{
                    def data = [
                        "firstName": "Irfan"
                        "lastName": "Luthfi"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
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

   
