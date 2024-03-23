pipeline {
    agent any
    
    stages {
        stage('Fetch Crumb') {
            steps {
                script {
                    // Fetch the crumb from Jenkins
                    CRUMB = sh(script: "curl -s 'http://3.111.34.178:8080/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,\":\",//crumb)'", returnStdout: true).trim()
                }
            }
        }
        stage('Build') {
            steps {
                // Your build steps here
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                // Your test steps here
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                // Your deployment steps here
                echo 'Deploying...'
            }
        }
    }
    
    post {
        success {
            script {
                // Create a tag in GitHub using Jenkins credentials
                withCredentials([usernamePassword(credentialsId: '59925bcf-2f2d-4485-9fe3-18a1331ba435', usernameVariable: 'adithyaacgacg3@gmail.com', passwordVariable: 'Adithya.sai@3427')]) {
                    sh "git tag -a release-${BUILD_NUMBER} -m 'Release ${BUILD_NUMBER}'"
                    sh "git push --tags --force --quiet https://github.com/Adithyasai123/jenkinsdemo.git"
                }
            }
        }
    }
}
