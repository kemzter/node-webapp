pipeline {
   agent { label 'linux-node' }
   stages {
     stage ('setup') {
       steps {
         sh "docker build -t my-image:${env.BUILD_ID} ."
       }
     }
     stage ('deploy') {
       steps {
	 sh "docker run -d -p 3000:3000 my-image:${env.BUILD_ID}"
       }
     }
   }
}
