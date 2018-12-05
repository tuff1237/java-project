properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		sh 'ant'
		junit 'reports/result.xml'
		sh 'ant -f test.xml -v 
		git 'https://github.com/tuff1237/java-project.git'
		sh 'ant -buildfile test.xml'   
	}   
	stage('Build') {    
		sh 'ant'
		sh 'ant -f build.xml 
	}   
	stage('Deploy') {    
		git 'https://github.com/tuff1237/java-project.git'
		sh 'ant -buildfile test.xml'   
	}   		
	stage('Results') {    
		junit 'reports/*.xml'   
	}
}
