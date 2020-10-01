pipeline {
    agent none 
    stages {
        stage('Build'){
            agent {
              kubernetes {
        label podlabel
        yaml """
kind: Pod
metadata:
  name: jenkins-agent
spec:
  containers:
  - name: kaniko
    image: ubuntu
    imagePullPolicy: Always
    command:
    - /bin/bash
    tdty: true
  restartPolicy: Never

"""
   }
            }
            steps {
                sh 'echo $PATH'
            }
        }
    }
}
