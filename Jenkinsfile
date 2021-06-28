pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/hazimastan/TestPyproject.git']]])
            }
        }
        stage('RunPython') {
            steps {
                bat 'more test.txt'
            }
        }
        stage('Test') {
            steps {
                echo "test"
            }
        }
    }
}