 
pipeline {
    agent any

    stages {
        stage('Fetch Crumb') {
            steps {
                script {
                    // Fetch the crumb from Jenkins
                    CRUMB = sh(script: "curl -s 'http://your-jenkins-url/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,\":\",//crumb)'", returnStdout: true).trim()
                }
            }
        }
        stage('Trigger Webhook') {
            steps {
                script {
                    // Include the crumb in the webhook request
                    sh "curl -X POST -H '$CRUMB' 'http://your-jenkins-url/github-webhook/'"
                }
            }
        }
    }
}

