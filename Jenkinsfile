pipeline{
    agent any
    def mvnHome = tool 'M2_HOME'
    stages {
            stage('Hello') {
                steps {
                    sh "echo $USER"
                    sh'docker version'
                    sh 'pwd'
                    sh 'ls -la'
                }
            }
//             stage('Delete workspace before') {
//                 steps {
//                     echo 'deleting workspace'
//                     deleteDir()
//                 }
//             }
            stage ('maven build') {
                steps {
                     echo 'maven build'
                     echo '${M2_HOME}'
                     sh '${M2_HOME}/bin/mvn clean compile'
                }

            }
     }
//             stage('Code Checkout') {
//                 steps {
//                     checkout([
//                         $class: 'GitSCM',
//                         branches: [[name: 'main']],
//                         userRemoteConfigs: [[
//                             credentialsId: 'github-jenkins',
//                             url: 'git@github.com:rovetskii/jenkins-test.git']]
//                     ])
//                     sh 'pwd'
//                     sh 'ls -la'
//                 }
//             }
}