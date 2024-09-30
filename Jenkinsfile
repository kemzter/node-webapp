pipeline {
    agent { label 'linux-node' }
    stages {
        stage ('setup') {
            steps {
                script {
                    sh "docker kill nodeapp || true"
                    docker.build("my-image:${env.BUILD_ID}")
                }
            }
        }
        stage ('deploy') {
            steps {
                script {
                    docker.image('my-image:${env.BUILD_ID}').run('--name nodeapp -p 3000:3000 -d')
                }
            }
        }
    }
}
