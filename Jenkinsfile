pipeline {
   agent { label 'linux-node' }
   stages {
     stage ('setup') {
       steps {
	 scripts {
	   sh "docker kill nodeapp || true"
	   docker.build("my-image:${env.BUILD_ID}")
	 }
       }
     }
     stage ('deploy') {
       steps {
         scripts {
	   docker.image('my-image:${env.BUILD_ID}').withRun('--name nodeapp -p 3000:3000 -d')
	 }
       }
     }
   }
}
