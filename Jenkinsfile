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
        stage('Setup parameters') {
            steps {
                script {
                    properties([
                        parameters([
//                             choice(
//                                 choices: ['ONE', 'TWO'],
//                                 name: 'PARAMETER_01'
//                             ),
                            booleanParam(
                                defaultValue: true,
                                description: 'Include tests',
                                name: 'isTest'
                            )
//                             text(
//                                 defaultValue: '''
//                                 this is a multi-line
//                                 string parameter example
//                                 ''',
//                                  name: 'MULTI-LINE-STRING'
//                             ),
//                             string(
//                                 defaultValue: 'scriptcrunch',
//                                 name: 'STRING-PARAMETER',
//                                 trim: true
//                             )
                        ])
                    ])
                }
            }
        }


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
            stage ('COMPILE') {
                  steps {
                      sh 'mvn clean package -DskipTests'
                      sh 'ls -la'
                  }
            }
            stage ('Test') {
                when {
                    expression {
                            params.isTest == true
                    }
                }
                  steps {
                      sh 'mvn test'
                  }
            }
            stage ('BUILD') {
                steps {
//                     dir('jenkins-test') {
                        sh 'pwd'
                        sh 'ls -la'
                        sh 'docker -v'
                        sh 'docker build -t irovetskyi/jenkins-test:0.0.2 .'
                        sh 'docker images'
//                     }
                }
            }
            stage ('Push') {
                steps {
                    withDockerRegistry(credentialsId:'jenkins-hub', url:'https://index.docker.io/v1/') {
                        sh 'docker push irovetskyi/jenkins-test:0.0.2'
                    }

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