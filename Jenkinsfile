pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                  containers:
                  - name: node 
                    image: node:18  
                    command:
                    - cat
                    tty: true
            '''
        }
    }

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
