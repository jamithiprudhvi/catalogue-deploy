pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        packageVersion = ''
        nexusURL = '172.31.2.43:8081'
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'What is the artificate version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is the anvironment?')


    }
    Build
    stages {
        stage('print version') {
            steps {
                sh """
                    echo "version: ${params.version}
                    echo "environment: ${params.environment} 
                """
            }
        }
        
    }
    // post Build
    post { 
        always { 
            echo 'I will always say Hello again'
            deleteDir()
        }
        failure { 
            echo 'This runs when pipeline is failed, used generally to send some alerts'
        }
        success { 
            echo 'It will say hello when pipe line is success'
        }
    }
}