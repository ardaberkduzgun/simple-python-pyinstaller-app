pipeline {
    
    agent any
    tools{
        tool name: 'MyDocker', type: 'dockerTool'
        tool name: 'Python3', type: 'jenkins.plugins.shiningpanda.tools.PythonInstallation'
    }
    environment{
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
            agent { docker { image 'Python3' } }
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
}