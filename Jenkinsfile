properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/tuff1237/java-project.git'
		sh 'ant'		
		sh 'ant -f test.xml -v'	
		junit 'reports/result.xml'		 
	}   
	stage('Build') {    
		sh 'ant'  
		sh ' ant -f build.xml'
	}   
	stage ('Report'){    
		sh 'aws cloudformation describe-stack-resources --stack-name Jenkins --region us-east-1' 
	}
}
