pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: build
    image: 'maven:3.8.3-jdk-11'
    command:
    - cat
    tty: true
    '''
        defaultContainer 'build'
        }
    }

    stages {
        stage('Sending notification') {
            steps {
                echo 'sending json data for unit testing in downstream job'
                publishEvent jsonEvent('{"unitTestEnable": "true", "environment": "prod"}')
            }
        }
    }
}