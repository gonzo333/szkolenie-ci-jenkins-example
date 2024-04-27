pipeline {
    agent any

    tools {
        maven "maven-3"
    }

    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh("git config --global user.email \"jenkins@codomi.pl\"")
                sh("git config --global user.name \"Jenkins\"")
                git 'https://github.com/rechandler12/test.git'
                sh 'mvn -B release:prepare -Dusername=xyz -Dpassword=xyz'
                sh("mvn -B release:perform -Dgoals='verify -DskipTests'")
            }
        }
    }
}
