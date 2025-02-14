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
            '''
            defaultContainer 'node'
        }
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
        stage('OWASP dependencies check') {
            steps {
                dependencyCheck additionalArguments: '''
                    --scan \'./\'
                    --out \'./\'
                    --format \'ALL\'
                    --prettyPrint''', odcInstallation: 'OWASP-DepCheck-10'
            }
        }
    }
}