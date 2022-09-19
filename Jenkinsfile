pipeline {
    agent any 	
//         environment {
// 		DOCKERHUB_CREDENTIALS=credentials('bhavi')
// 	}

	environment {
		
		PROJECT_ID = 'astute-might-359211'
                CLUSTER_NAME = 'cluster-1-clone-1'
                LOCATION = 'asia-south1-a'
                CREDENTIALS_ID = 'jenkins-pro'		
	}
	
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
            withCredentials([string(credentialsId: 'docker-push', variable: 'TOKEN')]) {
            sh 'docker login -u balraj0017 -p $TOKEN'

            sh 'docker push balraj0017/app:latest'
        }

       }
            }
            
            stage('Deploy to kubernetes'){
        steps{
            
            step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'app.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
		  
        }
       }
            
    }
}
            
         

