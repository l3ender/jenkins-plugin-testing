/* groovylint-disable CompileStatic, NestedBlockDepth */

pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '30'))
        disableConcurrentBuilds(abortPrevious: true)
        parallelsAlwaysFailFast()
        skipDefaultCheckout()
        timeout(time: 1, unit: 'HOURS')
        timestamps()
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
