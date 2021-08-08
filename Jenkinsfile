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
        			sh './install.sh'
      			}
    		}
    		stage('Test'){
      			steps{
				sh 'python -m unittest'
      			}
   		}
	}
}
			
