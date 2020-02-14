pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/arunimaU/Trading-UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			npm run build
			npm audit fix
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.31/webapps
             curl -u admin:admin http://13.127.242.124:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
