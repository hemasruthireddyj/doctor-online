pipeline{
    agent any
       stages{
           stage("git"){
               steps{
               git branch: 'main', credentialsId: 'hemasruthireddyj@gmail.com', url: 'https://github.com/hemasruthireddyj/doctor-online'
               }
           }
           stage("maven build"){
             steps{
                 sh "mvn clean package"
             }
           }
           stage("deploy"){
               steps{
                    sshagent(['tomcatt']) {
                    // COPY WAR FILE TO TOMCAT
                    sh "scp -o StrictHostKeyChecking=no target/doctor-online.war ec2-user@3.238.73.64:/opt/tomcat9/webapps"
                    // Stop tomcat
                    sh "ssh ec2-user@3.238.73.64/opt/tomcat9/bin/shutdown.sh"
                    // start tomcat
                    sh "ssh ec2-user@3.238.73.64 /opt/tomcat9/bin/startup.sh"

               }
           }
       }
       }
}
