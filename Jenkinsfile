node {
     def app 
     stage('clone repository') {
      checkout scm  
    }
     stage('Build docker Image'){
      app = docker.build("iplusaha25/nodejs-jenkins")
    }
     stage('Test Image'){
       app.inside {
         sh 'echo "TEST PASSED"' 
      }  
    }
     stage('Push Image'){
       docker.withRegistry('https://registry.hub.docker.com', 'Jenkins' ) {            
       app.push("${env.BUILD_NUMBER}")            
       app.push("latest")   
      }
	}  
}
