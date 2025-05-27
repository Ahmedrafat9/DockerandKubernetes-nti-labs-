pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building branch ${env.BRANCH_NAME}"
            }
        }
    stage('Show Fetched Branches') {    
        steps {
                script {
                    echo "Current Branch: ${env.BRANCH_NAME}"
                    sh '''
                        echo "All fetched branches:"
                        git branch -r
                    '''
                }
            }
        }
    }
}
