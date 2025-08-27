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
            mail to: 'deekshiya.n@gmail.com, zenmentors@guvi.in',
                 subject: "SUCCESS: Jenkins Build #${env.BUILD_NUMBER}",
                 body: "The Jenkins pipeline build was successful!"
        }
        failure {
            mail to: 'deekshiya.n@gmail.com',
                 subject: "FAILURE: Jenkins Build #${env.BUILD_NUMBER}",
                 body: "The Jenkins pipeline build failed. Check console output."
        }
    }
}

EOF

git init
git add .
git commit -m "Initial commit: script + Jenkinsfile"
git branch -M main
# create an empty repo on GitHub first, then set the remote:
git remote add origin https://github.com/<YOUR_GH_USERNAME>/<YOUR_REPO>.git
git push -u origin main   # use a GitHub Personal Access Token if prompted

