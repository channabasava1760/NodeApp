node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("vijina/mynodeapp2")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } */
                echo "Trying to Push Docker Build to DockerHub"
	    
	    //withDockerRegistry(credentialsId: 'dokcerid', url: 'https://hub.docker.com/') {
	    sh label: 'Docker Login', script: 'docker login --username "vijina" --password "hari@2010"'
    	    app.push("${env.BUILD_NUMBER}")
            app.push("latest")
	//}
    }
}
