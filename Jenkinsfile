pipeline{
	agent {label 'master'}
	tools{ maven 'M3'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'master', url: 'https://github.com/AnjuMeleth/flasky.git'
			}
		}
    stage('Setup'){
      steps{
        sh '''#!/bin/bash
                 echo "hello world" 
                 sh 'sudo apt update'
        sh 'sudo apt-get -y install python3-pip python3-dev build-essential libssl-dev libffi-dev python3-setuptools'
        sh 'sudo apt update'
        sh 'sudo apt-get -y install libmysqlclient-dev'
        sh 'pip3 install wheel'
        sh 'sudo apt -y install python3-venv'
        sh 'python3 -m venv myprojectenv'
        sh '#!/bin/bash'
        sh 'source myprojectenv/bin/activate'
        sh 'pip install -r requirements/dev.txt'
        sh 'export FLASK_APP=flasky.py'
        sh 'export FLASK_DEBUG=1'
         '''
