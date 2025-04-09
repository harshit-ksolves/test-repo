pipeline {
    agent any
    
    triggers {
        pollSCM('H/5 * * * *') // Polls every 5 minutes as backup (optional)
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/username/repo.git']]
                         ])
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building public repository code...'
                // Add your build commands here
                // Example: sh 'npm install' for Node.js projects
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: sh 'npm test'
            }
        }
        
        stage('Notify') {
            steps {
                echo 'Notifying about build success'
                // Could add Slack or email notifications here
            }
        }
    }
}