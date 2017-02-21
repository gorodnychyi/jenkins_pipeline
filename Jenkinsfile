pipeline {
    agent any
    stages {
        stage('Test task') {
            steps {
                echo 'Works!'
                sleep 5
                sh 'echo "OK"'
                echo 'Continue'
            }
        }
        stage('2nd stage tasks'){
            steps {
                echo '2nd - 1step'
                sh 'echo "2nd - 2"'
            }
        }
        stage('3') {
            steps {
                echo '3'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
            sh 'echo "1" >> /tmp/myfile'
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
