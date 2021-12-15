pipeline{
	agent{label 'master'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'vault', url: 'https://github.com/lohanichaten/Media99.git'
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
		stage('invoke playbook'){
      			steps{
				ansiblePlaybook become: true, credentialsId: 'ansible', installation: 'A2', inventory: '~/.ansible/hosts', playbook: './app_playbook.yml', vaultCredentialsId: 'valutid1'            			}
   		}
	}
}
