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
				sh 'python --version' 
				//sh 'python -m pip install --upgrade pip'
				//sh 'python --version' 
      			}
    		}
    		stage('Test'){
      			steps{
				sh 'python -m unittest'
      			}
   		}
		stage('Run'){
      			steps{
				sh 'flask run --host 0.0.0.0'
      			}
   		}
	}
}
			
