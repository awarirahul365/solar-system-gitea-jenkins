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
        }
    }

    stages {  
        stage('VM Node version') {
            steps {
                container('node') {
                    sh '''
                        ls -R
                        node -v
                        npm -v
                    '''
                }
            }
        }
    }
}