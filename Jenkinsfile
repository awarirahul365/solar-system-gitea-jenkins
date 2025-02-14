pipeline {
    agent any
    tools{
        nodejs 'nodejs-22-6-0'
    }
    environment{
        MONGO_URI="mongodb+srv://supercluster.d83jj.mongodb.net/superData"
        MONGO_USERNAME="superuser"
        MONGO_PASSWORD="superpassword"
        JUNIT_REPORT_PATH="test-results.xml"  // Add this to specify the output file
    }
    stages {  
        stage('Node Version and checkout') {
            steps {
                sh '''
                    ls -R
                    node -v
                    npm -v
                '''
            }
        }
        stage('Install dependencies') {
            steps {
                sh '''
                    npm install --no-audit
                '''
            }
        }
        stage('Unit Testing'){
            steps{
                sh '''
                    echo "MongoDB URI from env: $MONGO_URI"
                    echo "MongoDB USERNAME from env: $MONGO_USERNAME"
                    echo "MongoDB PASSWORD from env: $MONGO_PASSWORD"
                    npx mocha app-test.js --timeout 10000 --reporter mocha-junit-reporter --reporter-options mochaFile=test-results.xml --exit
                '''
                junit allowEmptyResults: true, testResults: 'test-results.xml'
            }
        }
    }
    post {
        always {
            cleanWs()  // Clean workspace after build
        }
    }
}