pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                    echo "Jenkins Pipeline Report" > report.txt
                    echo "Job Name: $JOB_NAME" >> report.txt
                    echo "Build Number: $BUILD_NUMBER" >> report.txt
                    echo "Build Date: $(date)" >> report.txt

                    echo "Build completed successfully" > build.log

                    echo "Application=25aug" > config.txt

                    echo "Created files:"
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    test -f report.txt
                    test -f build.log
                    test -f config.txt

                    echo "All tests passed!"
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'report.txt, build.log, config.txt'
        }
    }
}

