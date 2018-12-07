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
		wwithCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '5c634366-5d7d-4897-9573-da96774512e0', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    		// some block
		sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
		}
	}
}
