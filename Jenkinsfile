pipeline {
    agent {
	    label 'agent1'
	}
    environment {
       admin = "devops"
       mvn = "/opt/apache-maven-3.8.1/bin/mvn"
   }

    tools {
       maven "MVN"
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
                //sh "/opt/apache-maven-3.8.1/bin/mvn clean install package"
	      sh '"$mvn" -Dmaven.test.failure.ignore=true clean install package'
               }
            }
        stage ('Deploy to container'){
            steps {    
                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://3.82.214.173:8080/')], contextPath: 'webapp/target', war: 'webapp/target/*.war'
             }
        }
        stage ('Test'){
            steps {    
                sh "echo $admin"
             }
          }
      
    }
}
