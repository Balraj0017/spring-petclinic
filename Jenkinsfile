pipeline {
    agent any 	
//         environment {
// 		DOCKERHUB_CREDENTIALS=credentials('bhavi')
// 	}

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
           
// 	   stage('Build') { 
//                 steps {
//                   sh 'mvn clean package'
//                 }
//            }
	    
	   stage('build & run') { 
		steps {
		  sh './mvnw clean package'
		}
	   }
            
//             stage('Docker build'){
//          steps{
           
//                  sh 'docker build -t balraj0017/app1:latest .'
//              }
//        }
            stage('Docker push'){
        steps{
            withCredentials([string(credentialsId: 'bhavi', variable: 'TOKEN')]) {
            sh 'docker login -u balraj0017 -p $TOKEN'

            sh 'docker push balraj0017/app:latest'
        }

       }
            }
            
    }
}
