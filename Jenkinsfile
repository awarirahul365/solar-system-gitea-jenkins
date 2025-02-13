pipeline {
    agent any
    stages {
        stage('VM Node version') {
            step {
                sh '''
                    node -v
                    npm -v
                '''
            }
        }
    }
}