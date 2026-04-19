pipeline {
    agent any

    stages {
        stage('codescan') {
            steps {
                sh 'sudo yum install -y trivy'
                sh 'trivy --version'
                sh 'echo "trivy installed"'
                
            }
        }
        stage('dockerversion') {
            steps {
                sh 'docker -v'
            }
        }
        stage('checkcontainer') {
            steps {
                sh 'docker ps -a'
                
            }
        }
    }
    
}