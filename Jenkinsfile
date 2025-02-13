pipeline {
    agent any
    stages {
        stage('VM Node version') {
            steps {
                sh '''
                    node -v
                    npm -v
                '''
            }
        }
    }
}