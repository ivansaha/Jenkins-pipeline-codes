pipeline {
    agent any

    stages {
        stage('codescan') {
            steps {
                sh 'trivy fs . -o result.html'
                
            }
        }
        stage('dockerImageBuild') {
            steps {
                sh 'aws ecr get-login-password --region us-east-1 | \
                docker login --username AWS \
                --password-stdin 801296747126.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker build -t jenkins-repo .'
                sh 'docker build -t imageversion .' 
                sh 'docker tag jenkins-repo:latest 801296747126.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:latest'
                sh 'docker tag imageversion 801296747126.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:v.$BUILD_NUMBER'
                sh 'docker push 801296747126.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:latest'
                sh 'docker push 801296747126.dkr.ecr.us-east-1.amazonaws.com/jenkins-repo:v.$BUILD_NUMBER'
            }
        }
        stage('checkcontainer') {
            steps {
                sh 'docker ps -a'
                
            }
        }
    }
    
}