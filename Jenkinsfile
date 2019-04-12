pipeline{
    agent 'any'
    environment{
        GIT_TAG = null
    }
    stages{
        stage('Init'){
            steps{
                checkout scm;
            }
        }
        stage("Second"){
            steps{
                echo "Is there a tag?..."
                script{
                    GIT_TAG = bat(returnStdout: true, script: "@git tag --contains").trim()
                }
                echo sh(returnStdout: true, script: 'env') 
            }
        }
        stage('Tag Step'){
            when{
                expression{
                    "GIT_TAG" != ""
                }
            }
            steps{
                echo "It entered Tag Stage..."
            }
        }
    }
}