pipeline {
    
    agent any
   
    environment{
        DOCKER_HOME = tool name: 'MyDocker', type: 'dockerTool'
        PYTHON_HOME = tool name: 'Python3', type: 'jenkins.plugins.shiningpanda.tools.PythonInstallation'
        test="testtesttest"
    }
         
    stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${PATH}"
                echo "Test variable is: ${test}"
            }
        }
        stage('SCM Checkot'){
            steps{
                echo "Hello world!"
                git 'https://github.com/ardaberkduzgun/simple-python-pyinstaller-app'
            }
        }
    
        stage('Build') { 
            //agent { docker { image 'python:2-alpine' } }
            steps {
                sh 'python --version'
            }
        }
        stage('Test'){
            steps{
                echo 'Test stage'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy stage'
            }
        }
    }
}
