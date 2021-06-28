library "shared-library@${PipelineBranch}"

def stageData = ['parallel1','parallel2']

def generateStage(stageId) {
    return {
        stage("Parallel: ${stageId}") {
                echo "This is ${stageId}."
                build job: 'ParallelTest', wait: true, parameters: [string(name: 'stageId', value: stageId)], propagate: false
        }
    }
}


pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout()
                }                
            }
        }
        stage('RunPython') {
            steps {
                bat 'more test.txt'
            }
        }
        stage('ParallelMain') {
            steps {
                script {
                    parallel stageData.collectEntries { ["${it}" : generateStage(it)] }
                }
            }
        }
        stage('Final') {
            steps {
               echo "Delete Workspace"
               cleanWs()
            }
        }
        
    }
}
