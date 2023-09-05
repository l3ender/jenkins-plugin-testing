/* groovylint-disable CompileStatic, NestedBlockDepth */

pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

    stages {
        stage('Initialize job and checkout source') {
            steps {
                script {
                    sh 'printenv'
                    if (env.CHANGE_ID) {
                        echo "change ID: ${env.CHANGE_ID}"
                    } else {
                        echo 'no change ID!'
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                currentBuild.setDescription("${env.BRANCH_NAME}-SNAPSHOT")
            }
        }
    }
}
