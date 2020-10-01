pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                kubernetes {
                    label podlabel
                    yaml """
kind: Pod
metadata:
  name: jenkins-agent
spec:
  containers:
  - name: python
    image: python:2-alpine
    imagePullPolicy: Always
    command:
    - /bin/ash
    tty: true
  restartPolicy: Never
"""
                }
            }
            steps {
                sh 'python --version'
                stash(name: 'compiled-results', includes: 'sources/*.py*')
            }
        }
    }
}
