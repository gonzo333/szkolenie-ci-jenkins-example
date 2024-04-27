pipeline {
    agent any
   tools {
        maven 'maven-3'
    }
    stages {
        stage('Clean') {
            steps {
               cleanWs()
            }
        }
        
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic'
                sh 'mvn clean verify'
            }
        }
    }
    
    post {
        always {
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
        }
        success {
            script {
                slackSend color: '#36a64f', message: "Build successful! :white_check_mark:\nBUILD_TAG: ${env.BUILD_TAG}\nBUILD_URL: ${env.BUILD_URL}", channel: '#jenkins-pawel-nowaczek'
            }
        }
        failure {
            script {
                slackSend color: '#ff0000', message: "Build failed! :x:\nBUILD_TAG: ${env.BUILD_TAG}\nBUILD_URL: ${env.BUILD_URL}", channel: '#jenkins-pawel-nowaczek'
            }
        }
        unstable {
            script {
                slackSend color: '#ffff00', message: "Build unstable! :warning:\nBUILD_TAG: ${env.BUILD_TAG}\nBUILD_URL: ${env.BUILD_URL}", channel: '#jenkins-pawel-nowaczek'
            }
        }        
    }
}
