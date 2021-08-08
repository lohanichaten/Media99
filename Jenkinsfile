pipeline{
	agent{label 'master'}
	environment {
        	FLASK_DEBUG=1
		FLASK_APP="flasky.py"
		
    	}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'master', url: 'https://github.com/AnjuMeleth/flasky.git'
			}
		}
    		stage('Setup'){
      			steps{
				sh 'chmod +x install.sh'
        			sh './install.sh'
				//sh 'python --version' 
				//sh 'python -m pip install --upgrade pip'
				//sh 'python --version' 
      			}
    		}
    		stage('Test'){
      			steps{
				 sh '''#!/bin/bash
				     source myprojectenv/bin/activate	
                		     python -m unittest
				     '''
               			}
   		}
		stage('Build image'){
			steps{
				//tool name: 'D1', type: 'dockerTool'
				sh ''' 
					docker build -t anjurose/test . + ":$BUILD_NUMBER
					'''
			}
		}
				//withDockerRegistry(credentialsId: 'HubID1', url: 'https://hub.docker.com/'){
					//sh 'docker build
		stage('Run'){
      			steps{
				sh '''#!/bin/bash
				     source myprojectenv/bin/activate 
				     flask run --host 0.0.0.0
				     '''
      			}
   		}
	}
}
			
