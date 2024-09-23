pipeline {
   agent { label 'linux-node' }
   stages {
     stage ('setup') {
       steps {
	 script {
	   docker.build("my-image:${env.BUILD_ID}")
	 }
       }
     }
     stage ('deploy') {
       steps {
	 sh "docker run -p 3000:3000 my-image:${env.BUILD_ID}"
       }
     }
   }
}
