pipeline {
	agent any

	environment {
		NAME = "PipeLine"
	}
	

	stages {
		
		stage('Build') {
			steps {
				sh '''
					echo "---------------------Build Started----------------------"
					ls -la
					cat index.html
					echo "Build by Jenkins build# $BUILD_ID" >> index.html
					cat index.html
					echo "---------------------Build Finished----------------------"
				'''
			}
		}
		stage('Test') {
			steps {
				sh '''
					echo "---------------------Test Started----------------------"
					result=`grep "Hello" index.html |wc -l`
					echo $result
					if  [ "$result" = "1" ]
					then
					 echo "Test Passed"
					else	
					 echo "Test Failed"
					 exit 1
					fi
					echo "---------------------Test Finished----------------------"
				'''
			}
		}
		stage('Deploy') {
			steps {
				sh '''				
					echo "---------------------Deployment Started----------------------"
					ls -la
					cp -f index.html /var/www/html/index.html
					echo "---------------------Deployment Finished----------------------"
				'''
			}
		}
	}
}