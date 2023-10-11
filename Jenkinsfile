pipeline{
    agent any
    parameters {
  choice choices: ['dev', 'test', 'prod'], description: 'choose the environment to deploy', name: 'envname'
}
 stages{
           stage("maven build"){
             steps{
                 sh "mvn clean package"
             }
           }
       }
}
