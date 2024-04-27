pipeline {
    agent any

    tools {
        maven "maven-3"
    }

    stages {
        stage('Build') {
            steps {
                cleanWs()
                sh("git config --global user.email \"pawelnowaczek88@gmail.com\"")
                sh("git config --global user.name \"gonzo333\"")
                sh("git config --global user.pass \"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\"")
                git 'https://github.com/gonzo333/test.git'
                sh 'mvn -B release:prepare -Dusername=xyz -Dpassword=xyz'
                sh("mvn -B release:perform -Dgoals='verify -DskipTests'")
            }
        }
    }
}
