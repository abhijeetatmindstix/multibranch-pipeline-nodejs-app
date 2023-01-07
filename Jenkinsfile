pipeline {
    agent {
        node {
            label 'master'
        }
    }
    environment {
        PATH = "/opt/homebrew/bin:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}
