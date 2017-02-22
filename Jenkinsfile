pipeline {
    agent any
    stages {
        stage('Edit project files') {
            steps {
                sh 'echo "echo \"version: ${release}\"" >> /home/jenkins/rpms/my-tools-pack/root/usr/local/bin/stat.sh'
            }
        }
        stage('Increase release version') {
            steps {
               sh 'sed -i "s/Release.*$/Release: ${release}/" /home/jenkins/rpms/my-tools-pack/spec/header' 
            }
        }
        stage('Build package'){
            steps {
                sh 'cd /home/jenkins/rpms/my-tools-pack/; togo build package'
            }
        }
        stage('Update package in system') {
            steps {
                sh 'sudo yum install /home/jenkins/rpms/my-tools-pack/rpms/my-tools-pack-1.0-${release}.noarch.rpm -y'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
            sh '/usr/local/bin/stat.sh'
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
