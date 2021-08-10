pipeline{
	agent{label 'master'}
	environment {
        	FLASK_DEBUG=1
		FLASK_APP="flasky.py"
		registry = "anjurose/test" 
	        registryCredential = 'HubID1' 
	        dockerImage = '' 
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
				tool name: 'D1', type: 'dockerTool'
				script { 
					dockerImage = docker.build registry + ":$BUILD_NUMBER" }
			}
		}
		stage('Deploy our image') { 
    		        steps { 
			       script { 
		               		docker.withRegistry( '', registryCredential ) { 
					dockerImage.push() }
			       }
                	} 
	            }
		/*stage('TestRun'){
      			steps{
				sh '''#!/bin/bash
				     source myprojectenv/bin/activate 
				     flask run --host 0.0.0.0
				     '''
      			}
   		}*/
		stage('DockerDeploy'){
      			steps{
				sh 'ansible -m ping -i ./inventory.yml all'
				ansiblePlaybook become: true, becomeUser: 'ubuntu', credentialsId: 'UbuntuID1', installation: 'A1', inventory: './inventory.yml', playbook: './app_playbook.yml'
      			}
   		}
	}
}
			
