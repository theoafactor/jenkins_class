pipeline {
    agent any
    stages {
        stage("starting"){
            steps{
                echo "This is for the starting stage"
            }
        }


         stage("building"){
            when{
                expression{
                    BRANCH_NAME == "testing"
                }
            }
            steps{
                script {
                    sh "ssh -i tester.key root@123.222.33.44"
                }
            }
        }

         stage("production"){
            steps{
                echo "This is for the prduction stage"
            }
        }

    }

      post{

            failure{
                emailext subject: "Everything FAILED",
                         body: """
                                This is the default body. ${env.JOB_NAME} - ${env.BUILD_NUMBER}, 
                                ${env.BUILD_URL}
                                ----------------
                                ${env.BUILD_LOG}
                                """,
                         to: "theoafactor@gmail.com"
                
            }

             success{
                emailext subject: "Everything works fine from here",
                         body: """
                                This is the default body. ${env.JOB_NAME} - ${env.BUILD_NUMBER}, 
                                ${env.BUILD_URL}
                                ----------------
                                ${env.BUILD_LOG}
                                """,
                         to: "theoafactor@gmail.com"
                
            }
        }
}