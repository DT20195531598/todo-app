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
                sh 'git clone https://github.com/DT20195531598/todo-app'
		// sh 'cd /todo-app'
            }
        }
        stage('file'){
            steps{
                script{
                    docker.build("${env.REGISTRY}/${env.IMAGE_NAME}:${env.VERSION}","./web")
                }
            } 
            }
        stage("push"){
            steps{
                script{
                    docker.withRegistry('https://index.docker.io/v1/','b9dc147c-ac9e-4c19-80e6-c306e1b524b6') {
                        docker.image("${env.REGISTRY}/${env.IMAGE_NAME}:${env.VERSION}").push()
                    }
                }
            }
        }
        
    }
}
