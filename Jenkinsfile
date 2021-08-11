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
				git branch: 'module4', url: 'https://github.com/AnjuMeleth/Media99.git'
			}
		}
    		stage('Setup'){
      			steps{
				sh 'chmod +x install.sh'
        			sh './install.sh'
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
					dockerImage = docker.build registry + ":latest" }
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
		stage('DockerDeploy'){
      			steps{
				ansiblePlaybook credentialsId: 'UbuntuID1', disableHostKeyChecking: true , installation: 'A1' , inventory: './inventory.yml', playbook: './app_playbook.yml'
      			}
   		}
	}
}
			
