pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'scp target/gamutkart.war root@172.31.46.36:/root/apache-tomcat-10.1.30/webapps'
	}
    }
}
}
