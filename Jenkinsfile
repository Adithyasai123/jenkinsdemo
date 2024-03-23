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
            // Create a tag in GitHub
            sh "git tag -a release-${BUILD_NUMBER} -m 'Release ${BUILD_NUMBER}'"
            sh "git push --tags --force --quiet https://adithyaacgacg3@gmail.com:Adithya.sai@3427/Adithyasai123/jenkinsdemo.git"
        }
    }
}

}
