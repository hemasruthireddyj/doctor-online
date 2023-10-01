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
                   sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcatt', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''
/opt/tomcat9/bin/shutdown.sh
/opt/tomcat9/bin/startup.sh''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'webapps', remoteDirectorySDF: false, removePrefix: 'target', sourceFiles: 'target/doctor-online.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])

               }
           }
       }
       
}
