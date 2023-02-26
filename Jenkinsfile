pipeline {
	agent any //where we are executing this script
	environment{
	    DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
		stages {
			stage('Cleanws') {
				steps {
					 cleanWs()
					}
			}
			
			stage('checking docker images') {
				steps {
					
					sshagent(['ec2-instance-key-pair']) {
						 
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker images'
						 
					}		  
				}
			}
			stage('Tagging Docker image') {
			    steps {
					
					sshagent(['ec2-instance-key-pair']) {
						 
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker tag nginx-app anilkumarnooludocker/nginx-app:${BUILD_ID}'
						 
					}		  
				}
			}
			stage('Pushing Docker images'){
			    steps {
					
					sshagent(['ec2-instance-key-pair']) {
						 
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker tag nginx-app anilkumarnooludocker/nginx-app:${BUILD_ID}'
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker images'
						 sh 'echo $DOCKERHUB_CREDENTIALS_PSW '
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
						 sh 'ssh -o StrictHostKeyChecking=no ${hostname} sudo docker push anilkumarnooludocker/nginx-app:${BUILD_ID}'
						 
					}		  
				}
			}
		}
}
			
