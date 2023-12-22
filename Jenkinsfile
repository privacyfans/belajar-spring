pipeline {
    agent any

    environment{
        AUTHOR = "Irfan Luthfi"
        COMPANY = "BWS"
        APP = credentials("irfan_credentials_id")
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'SECONDS')
    }

    // triggers {
    //     cron ("* * * * *")
    //     pollSCM("*/5 * * * *")
    //     upstream(upstreamProjects: 'job1,job2', threshold: hudson.model.Result.SUCCESS)
    // }
    // parameters {
    //     string(name: 'NAME', defaultValue: 'Guest', description: 'Whats is your name?')
    //     text(name: 'DESCRIPTION', defaultValue: '', description: 'Tell me about you')
    //     booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Need too deploy?')
    //     choice(name: 'SOCIAL_MEDIA', choices: ['Instagram','Facebook'], description: 'Whitch social media?')
    //     password(name: 'SECRET', defaultValue: '', description: 'Encrypt Key')
    // }


    stages {
        // stage('Parameter') {
        //     steps {
        //        echo("Hello: ${params.NAME}")
        //        echo("Description: ${params.DESCRIPTION}")
        //        echo("Deploy: ${params.DEPLOY}")
        //        echo("Social Media: ${params.SOCIAL_MEDIA}")
        //        echo("Secret: ${params.SECRET}")
        //     }
        // }
        
        stage('Pre-Build') {
            steps {
               echo("AUTHOR: ${AUTHOR}")
               echo("COMPANY: ${COMPANY}")
               echo("USERNAME: ${APP_USR}")
               //echo("PASSWORD: ${APP_PSW}")
               sh('echo "PASSWORD: $APP_PSW" > "rahasia.txt"')
               echo("Start Job: ${env.JOB_NAME}")
               echo("Start Job: ${env.BUILD_NUMBER}")
               echo("Start Job: ${env.BRANCH_NAME}")
            }
        }

        stage('Build') {
            steps {
                script{
                    for (int i = 0; i < 10; i++) {
                        echo ("Script ${i}")
                    }
                }
                echo 'Build Start'
                //sh("./mvnw clean compile test-compile")
                echo 'Build Stop'
            }
        }

        stage('Test') {
            steps {
                script{
                    def data = [
                        "firstName": "Irfan",
                        "lastName": "Luthfi"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                echo 'Test 1'
                //sh("./mvnw test")
                echo 'Test 3'
            }
        }

        stage('Deploy') {
            input {
                message "Can we deploy?"
                ok "Yes, of course."
                submitter "Irfan Luthfi Submitter"
                parameters {
                    choice(name: 'TARGET_ENV',choices: ['DEV', 'QA','PROD'], description: 'We will deploy to?')
                }
            }
            steps {
                echo "Deploy To: ${TARGET_ENV}"
                echo 'Deploy 1'
                echo 'Deploy 2'
                echo 'Deploy 3'
            }
        }

        stage('Release') {
           when {
            expression {
                return params.DEPLOY;
            }
           }
            steps {
              echo "Release it"
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

   
