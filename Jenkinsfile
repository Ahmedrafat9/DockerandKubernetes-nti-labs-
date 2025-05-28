pipeline {
    agent { label 'ec2-slave' }  // <-- use your EC2 agent label here

    stages {
        stage('Example') {
            steps {
                sh 'echo Running on EC2 slave node'
                sh 'uname -a'
                // your build or deploy steps here
            }
        }
    }
}