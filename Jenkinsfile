pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/gattem/hello-spring'
                sh "mvn package"
            }
            post {
                success {
                    archiveArtifacts 'target/hello-spring-0.1.0.jar'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Running commands to execute Test cases'
                sh 'exit 1'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS'
              }
            }
            steps {
                echo 'Running steps to deploy the jar file to nodes'
            }
        }
    }
}
