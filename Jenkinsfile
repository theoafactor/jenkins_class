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
                echo "This is for the building stage for testing branch "
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
                emailext subject: "Everything works fine from here",
                         body: "This is the default body",
                         to: "theoafactor@gmail.com"
                
            }

             success{
                emailext subject: "Everything works fine from here",
                         body: "This is the default body",
                         to: "theoafactor@gmail.com"
                
            }
        }
}