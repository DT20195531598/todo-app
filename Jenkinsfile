pipeline{
    agent any
    // tools {
       // nodejs 'NodeJs'
   // }
    environment {
        IMAGE_NAME = "threed"
        REGISTRY = "ramya2526"
        VERSION = "1.0.${env.BUILD_NUMBER}"
    }

    stages{
        stage('checkout'){
            steps{
		cleanWs()
                sh 'git clone https://github.com/DT20195531598/todo-app.git'
		// sh 'cd /todo-app'
		//sh 'apt-get install docker -y'
            }
        }
        stage('file'){
            steps{
                script{
                    // docker.build("${env.REGISTRY}/${env.IMAGE_NAME}:${env.VERSION}","./web")
		    sh 'cd web'
		    sh 'docker build -t ramya2526/threed:1.0.5 .'
                }
            } 
            }
        stage("push"){
            steps{
                script{
                    docker.withRegistry('https://index.docker.io/v1/','docker') {
                        docker.image("${env.REGISTRY}/${env.IMAGE_NAME}:${env.VERSION}").push()
                    }
                }
            }
        }
        
    }
}
