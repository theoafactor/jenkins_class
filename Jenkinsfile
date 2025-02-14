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
                    try {

                        sh "ssh -o -i tester.key root@123.222.33.44"

                    }catch(Exception err){
                        currentBuild.result = "FAILURE"

                        throw err
                    }
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
                script {
                    //def build_log = currentBuild.rawBuild.getLog(200).join("\n")
                    def build_log = Manager.build.log
                    emailext subject: "Everything FAILED",
                            body: """
                                    This is the default body. ${env.JOB_NAME} - ${env.BUILD_NUMBER}, 
                                    ${env.BUILD_URL}
                                    ----------------
                                    ${build_log}
                                    """,
                            to: "theoafactor@gmail.com"

                }
                
            }

             success{
                emailext subject: "Everything works fine from here",
                         body: """
                                This is the default body. ${env.JOB_NAME} - ${env.BUILD_NUMBER}, 
                                ${env.BUILD_URL}
                                ----------------
                            
                                """,
                         to: "theoafactor@gmail.com"
                
            }
        }
}