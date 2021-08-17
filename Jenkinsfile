
pipeline{
	agent{label 'master'}
	environment {
        	FLASK_DEBUG=1
		      FLASK_APP="flasky.py"
		   	}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'test', url: 'https://github.com/AnjuMeleth/Media99.git'
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
    stage('Deploy'){
      steps{
        sh 'scp 
	}
}
