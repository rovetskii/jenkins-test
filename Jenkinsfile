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
}