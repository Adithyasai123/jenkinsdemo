node{
    
    def mvnhome  = tool name : 'maven3.9.3', type:'maven'
    stage('checkout code'){git credentialsId: 'e9e442b6-d7a1-457c-b2af-2fbb5dee3e48', url: 'https://github.com/Adithyasai123/jenkinsdemo.git'}
    
    stage('Build')
                 {sh "$mvnhome/bin/mvn clean package"}
    stage('deploy to nexus')
                 {sh "$mvnhome/bin/mvn clean deploy"}
    stage('deploy to Tomcat'){
        sshagent(['TomcatServer']){
       sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.190.46:/opt/apache-tomcat-9.0.76/webapps/maven-web-application.war"
           }
       }
   
    
}
