properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/tuff1237/java-project.git'
		sh 'ant'		
		sh 'ant -f test.xml -v'		'		 
	}   
	
}
