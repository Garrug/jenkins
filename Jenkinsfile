
pipeline {
    agent any
    triggers {
        pollSCM('H/5 * * * *')
    }
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

        
    stage('Tests') {
        when {
            expression {
                return params.RUN_TESTS
            }
        }

        parallel {

            stage('Unit Tests') {
                steps {
                    echo 'Running unit tests...'
                    sleep(time: 3, unit: 'SECONDS')
                    echo 'Unit tests completed!'
                }
            }

            stage('Integration Tests') {
                steps {
                    echo 'Running integration tests...'
                    sleep(time: 5, unit: 'SECONDS')
                    echo 'Integration tests completed!'
                }
            }
        }
    }


        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
