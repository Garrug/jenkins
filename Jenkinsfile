
pipeline {
    agent any

    parameters {
        // Text parameter
        string(name: 'ENV', defaultValue: 'dev',
               description: 'Environment')

        // Choice parameter
        choice(name: 'VERSION',
               choices: ['1.0', '1.1', '2.0'],
               description: 'Application version')

        // Boolean parameter
        booleanParam(name: 'RUN_TESTS',
                     defaultValue: true,
                     description: 'Run tests')
    }

    stages {

        stage('Build') {
            steps {
                echo "Environment: ${params.ENV}"
                echo "Version: ${params.VERSION}"
                echo "Run tests: ${params.RUN_TESTS}"

                echo 'Building the application...'
            }
        }

        stage('Test') {
            when {
                expression {
                    return params.RUN_TESTS
                }
            }

            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
