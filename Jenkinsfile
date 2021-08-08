pipeline{
	agent {label 'master'}
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
			
