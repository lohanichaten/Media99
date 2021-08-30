pipeline{
	agent{label 'master'}
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
		stage('invoke playbook'){
      			steps{
				ansiblePlaybook credentialsId: 'UbuntuID1', disableHostKeyChecking: true, inventory: '/etc/ansible/hosts', installation: 'A1', playbook: './testplaybook.yml', vaultCredentialsId: 'VaultID1'               			}
   		}
	}
}
