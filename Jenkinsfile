pipeline {
    agent any
    tools{
        nodejs 'nodejs-22-6-0'
    }
    environment{
        MONGO_URI="mongodb+srv://supercluster.d83jj.mongodb.net/superData"
        MONGO_USERNAME="superuser"
        MONGO_PASSWORD="superpassword"
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
                    npm test
                '''
            }
        }
    }
}