def containerName="dockerimage"
def tag="latest"
 
node {
	 
    
  stage('Checkout Source Code') {
    checkout scm
  }

     stage('Build'){
        sh "mvn clean install"
    }

    stage("Image dockerimage"){
         sh "docker image dockerimage -f"
    }

    stage('Image Build'){
        sh "docker build -t $dockerimage:${env.BUILD_NUMBER} --pull --no-cache ."
        echo "Image build complete"
    }
    stage ('Run Application') {
    try {
      // Stop existing Container
       //sh 'docker rm $dockerimage -f'
      // Start database container here
      sh "docker run -d --name $dockerimage $dockerimage:${env.BUILD_NUMBER}"
    } 
	catch (error) {
    } finally {
      // Stop and remove database container here
      
    }
  }



     
	
 
}

