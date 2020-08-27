pipeline {
    
    agent none 
    stages {
        stage('Initialize')
    {
        def dockerHome = tool 'MyDocker'
      
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }
     stage('Push to Docker Registry'){
        steps {
            withCredentials([usernamePassword(credentialsId: 'dockerHubAccount', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {                
            pushToImage(CONTAINER_NAME, CONTAINER_TAG, USERNAME, PASSWORD)
            }            
        }  
        stage('Build') { 
            agent {
                docker {
                    image 'python:2-alpine' 
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
    }
}