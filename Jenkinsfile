pipeline {	
	agent any	tools {	    
		maven 'my-maven'		
		jdk 'my-jdk'	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/rohitha987/service-registry.git', branch:'main'}	
		}		
		stage('Build'){			
			steps {bat "mvn clean install -DskipTests"}		
		}		
		stage('Test'){			
			steps{bat "mvn test"}		}		
		}
		stage('Deploy') {			
			steps { bat "docker build -t servicereg-image ."			    
			            bat "docker run -p 8761:8761 -d --name servicereg-container servicereg-image"}		
		}		
	}
