pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './build.sh'
            }
        }
    }

    post {
        success {
            mail(
                to: 'deekshiya.n@gmail.com,zenmentors@guvi.in',
                subject: "SUCCESS: Jenkins Build #${env.BUILD_NUMBER}",
                body: "The Jenkins pipeline build was successful!"
            )
        }
        failure {
            mail(
                to: 'deekshiya.n@gmail.com',
                subject: "FAILURE: Jenkins Build #${env.BUILD_NUMBER}",
                body: "The Jenkins pipeline build failed. Check console output."
            )
        }
    }
}
