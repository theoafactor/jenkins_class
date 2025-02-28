pipeline {
    agent { label 'agent1'}
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
                echo "This is for the building stage"
                script {
                    def BUILD_NUMBER = "${env.BUILD_NUMBER}"
                }
               
            }
        }

         stage("production"){
            steps{
                echo "This is for the prduction stage"
            }
        }
    }
}