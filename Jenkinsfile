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
		sh "pwd"
		sh 'ls'
            }
        }
        stage('file'){
            steps{
                script{
                    // docker.build("${env.REGISTRY}/${env.IMAGE_NAME}:${env.VERSION}","./web")
		    sh 'cd todo-app/web'
		    sh 'ls -l'
		    sh 'docker build -t ramya2526/threed:${env.VERSION} ./todo-app/web'
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
