pipeline {
    agent any

    stages {

        stage('Plan Phase') {
            steps {
                echo 'Planning Phase has been initiated'
            }
        }

        stage('Code Checkout') {
            when {
                not {
                    branch 'master'
                }
            }
            steps {
                echo 'Fetching code from repository...'
            }
        }

        stage('Integration Phase') {
            steps {
                input 'Do you want to continue with the integration phase?'
            }
        }

        stage('Test Phase') {
            parallel {

                stage('Unit Test') {
                    steps {
                        echo 'Performing unit test...'
                    }
                }

                stage('Integration Test') {
                    steps {
                        echo 'Performing integration test...'
                    }
                }

                stage('Finalising Report') {
                    steps {
                        echo 'Finalising report...'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                timeout(time: 30, unit: 'SECONDS') {
                    echo 'Successfully deployed'
                }
            }
        }
    }
}