pipeline {
    agent any
	   // label 'agent1'
	//}
    environment {
       admin = "devops"
       }
    stages {
        stage ('Check-out'){
            steps {
                checkout scm
 	}
        }
        stage ('Build'){
            steps {
                sh "echo  clean install package"
		sh "/opt/apache-maven-3.8.1/bin/mvn clean  package"
	    }
            }
        stage ('Deploy to container'){
            steps {    
                //deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://3.82.214.173:8080/')], contextPath: 'webapp/target', war: 'webapp/target/*.war'
            sh "echo test" 
	    }
        }
        stage ('Test'){
            steps {    
                sh "echo $admin"
             }
          }
      
    }
}
