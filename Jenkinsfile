pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                echo 'Works!'
            }
            steps {
                echo 'Next step'
            }
            steps {
                echo 'Last one'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, the Pipeline was previously failing but is now successful'
        }
    }
}