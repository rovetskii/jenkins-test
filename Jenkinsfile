pipeline{
    agent any
//     def mvnHome = tool 'M2_HOME'
    tools {
        maven 'MAVEN_HOME'
    }
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
                   sh '''
                     echo 'maven build'
                     echo "MAVEN_HOME=${MAVEN_HOME}"
                     echo "PATH=${PATH}"
                     mvn -v

                    '''
                }
            }
            stage ('Build') {
                  steps {
                      sh 'mvn clean compile'
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