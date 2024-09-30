pipeline {
    agent { label 'linux-node' }
    stages {
        stage ('setup') {
            steps {
                script {
                    sh "docker kill nodeapp || true"
                    docker.build("my-image")
                }
            }
        }
        stage ('deploy') {
            steps {
                script {
                    docker.image('my-image').withRun('--name nodeapp -p 3000:3000') {}
                }
            }
        }
    }
}
