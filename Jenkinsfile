pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                    echo "===== BUILD STAGE STARTED ====="

                    mkdir -p package

                    echo "Application version 1.0" > package/app.txt
                    echo "Configuration data" > package/config.txt

                    zip -r application.zip package/

                    echo "===== BUILD COMPLETED ====="

                    ls -lh application.zip
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "===== TEST STAGE STARTED ====="

                    test -f package/app.txt
                    test -f package/config.txt

                    echo "All tests passed"

                    echo "===== TEST COMPLETED ====="
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "===== DEPLOY STAGE STARTED ====="

                    mkdir -p deployment

                    cp application.zip deployment/

                    echo "Application deployed successfully"

                    ls -lh deployment/
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully"

            archiveArtifacts artifacts: 'application.zip', fingerprint: true
        }

        failure {
            echo "Pipeline failed. Please check the failed stage."
        }

        always {
            echo "Pipeline execution finished."
        }
    }
}
