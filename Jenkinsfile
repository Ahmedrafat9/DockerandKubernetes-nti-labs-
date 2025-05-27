pipeline {
    agent any

    parameters {
        string(name: 'ENV', defaultValue: 'dev', description: 'Deployment environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests?')
        choice(name: 'BRANCH', choices: ['main', 'dev', 'feature'], description: 'Select Git branch')
    }

    stages {
        stage('Print Parameters') {
            steps {
                script {
                    echo "Environment: ${params.ENV}"
                    echo "Run Tests: ${params.RUN_TESTS}"
                    echo "Branch selected: ${params.BRANCH}"
                }
            }
        }
    }
}
