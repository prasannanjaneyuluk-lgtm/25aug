
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                    mkdir -p package

                    echo "Application version 1.0" > package/app.txt
                    echo "Configuration data" > package/config.txt

                    zip -r application.zip package/

                    ls -lh
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'application.zip'
        }
    }
}

