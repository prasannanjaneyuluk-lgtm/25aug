pipeline {
    agent any

    stages {

        stage('Create Different Files') {
            steps {
                sh '''
                    echo "This is a report" > report.txt
                    echo "This is a log" > application.log
                    echo "name=25aug" > config.properties

                    ls -la
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '*.txt, *.log, *.properties'
        }
    }
}

