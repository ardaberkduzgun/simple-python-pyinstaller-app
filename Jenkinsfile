pipeline {
    agent any
    environment{
        DOCKER_HOME = tool name: 'MyDocker', type: 'dockerTool'
        PYTHON_HOME = tool name: 'Python3', type: 'jenkins.plugins.shiningpanda.tools.PythonInstallation'
        test="testtesttest"
    }
    options {
        skipStagesAfterUnstable()
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
            //agent {
                //docker {
                //    image 'python:2-alpine'
                //}
            //}
            steps {
                sh 'python --version'
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
                stash(name: 'compiled-results', includes: 'sources/*.py*')
            }
        }
        stage('Test') {
            // agent {
            //     docker {
            //         image 'qnib/pytest'
            //     }
            // }
            // steps {
            //     sh 'py.test --junit-xml test-reports/results.xml sources/test_calc.py'
            // }
            // post {
            //     always {
            //         junit 'test-reports/results.xml'
            //     }
            // }
             steps{
                echo 'Test stage'
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy stage'
            }

        }
        stage('Deliver') { 
            // agent any
            // environment { 
            //     VOLUME = '$(pwd)/sources:/src'
            //     IMAGE = 'cdrx/pyinstaller-linux:python2'
            // }
            // steps {
            //     dir(path: env.BUILD_ID) { 
            //         unstash(name: 'compiled-results') 
            //        // sh "docker run --rm -v ${VOLUME} ${IMAGE} 'pyinstaller -F add2vals.py'" 
            //     }
            // }
            // post {
            //     success {
            //         archiveArtifacts "${env.BUILD_ID}/sources/dist/add2vals" 
            //         //sh "docker run --rm -v ${VOLUME} ${IMAGE} 'rm -rf build dist'"
            //     }
            // }
            steps{
                echo 'Deliver stage'
            }
        }
    }
}