pipeline{
    agent any
    stages {
            stage('Hello') {
                steps {
                    sh "echo $USER"
                    sh'docker version'
                    sh 'pwd'
                    sh 'ls -la'
                }
            }
            stage('Delete workspace before') {
                steps {
                    echo 'deleting workspace'
                    deleteDir()
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