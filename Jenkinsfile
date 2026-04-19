pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                sh 'echo "cloning repo"'
                sh 'whoami'
                sh 'uname -r'
            }
        }
        stage('test') {
            steps {
                sh 'echo "test"'
            }
        }
        stage('File-create') {
            steps {
                sh 'echo "create a file"'
                sh 'touch test-file-$BUILD_ID'
            }
        }
    }
    
}