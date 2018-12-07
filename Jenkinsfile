properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/tuff1237/java-project.git'
		sh 'ant -f test.xml -v'	
		junit 'reports/result.xml'		 
	}   
	stage('Build') {    
		sh ' ant -f build.xml'
	}  
	stage('Deploy') {
	sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://elasticbeanstalk-us-east-1-647341460024'
	}
	stage ('Report'){    
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '5c634366-5d7d-4897-9573-da96774512e0', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    		// some block
		sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
		}
	}
}
