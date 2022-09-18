pipeline {
    agent any 	
// 	environment {
		
// 		PROJECT_ID = 'third-fire-260721'
//                 CLUSTER_NAME = 'k8s-cluster'
//                 LOCATION = 'europe-north1-a'
//                 CREDENTIALS_ID = 'kubernetes'		
// 	}
	
    stages {	
	   stage('Scm Checkout') {            
		steps {
                  checkout scm
		}	
           }
           
	   stage('Build') { 
                steps {
                  echo "Cleaning and packaging..."
                  sh 'mvn clean package'
                }
           }
	    
	   stage('Test') { 
		steps {
	          echo "Testing..."
		  sh './mvnw clean package'
		}
	   }
    }
}
