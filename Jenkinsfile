pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                  containers:
                  - name: node 
                    image: node:22  
                    command:
                    - cat
                    tty: true
                  - name: java
                    image: openjdk:11
                    command:
                    - cat
                    tty: true
                    env:
                    - name: JAVA_HOME
                      value: /usr/local/openjdk-11
            '''
            defaultContainer 'node'
        }
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