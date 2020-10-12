
pipeline {
	agent any
	tools {
   	 
    	maven 'MAVEN_HOME-3.6.3'

	}
	/*environment {
    	DOCKER_SERVER = 'docker-registry.cdacmumbai.in:5000/discoveryserver.jar'
    	DOCKER_BE = 'docker-registry.cdacmumbai.in:5000/erp-admin-reimburse-be.jar'
    	DOCKER_FE = 'docker-registry.cdacmumbai.in:5000/erp-admin-reimburse-fe.jar'
          
	}*/

	stages {
    
    /*stage('Enviroment Variables'){
            steps{
                script{
               load "$JENKINS_HOME/workspace/Test/envar.groovy"        
            //  readProperties(file: "https://github.com/Sonali-K/ECGC-CI_CD/blob/master/envar.groovy").each {key, value -> env[key] = value }
            //sh "https://github.com/Sonali-K/ECGC-CI_CD/blob/master/envar.groovy"

                }
                
            }
            
        }*/

    /*	stage ('Initialization') {
        	steps {
            	sh '''
                	echo "PATH = ${PATH}"
           	 
            	'''
            	 //zAP Setup and Initialization
                script {
                    startZap(host: "${host}", port: "${port}", timeout:"${timeout}", zapHome: "${zapHome}",allowedHosts:["${allowedHosts}"]) // Start ZAP at /opt/zaproxy/zap.sh, allowing scans on github.com
                }
        	         
             }
    	    }*/

     	stage("Build"){
        	steps{
           	         

	git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_be.git',branch:'developer', credentialsId: 'GitLab-SSH-sonali123'
       	 
            	sh "mvn  compile"

	git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_fe.git', branch:'developer', credentialsId: 'GitLab-SSH-sonali123'
              	sh "mvn compile"	 
            	 
          	 
        	}
    	}
 
	 
 /*	stage('Code Analysis') {
  	steps {
    	script {
      	// requires SonarQube Scanner 2.8+
      	scannerHome = tool 'SonarQubeScanner'
    	}
    	withSonarQubeEnv('sonarqube') {
             
	git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_be.git',branch:'developer', credentialsId: 'GitLab-SSH-sonali123'
       	 
            	sh "mvn clean package sonar:sonar"
          
   git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_fe.git',branch: 'developer', credentialsId: 'GitLab-SSH-sonali123'
              	sh "mvn clean package sonar:sonar" 
    	}
  	}
	}*/

    
	/*stage('Unit Testing') {
        	steps{
          	script {


	git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_be.git',branch:'developer', credentialsId: 'GitLab-SSH-sonali123'

               	sh "mvn clean test"
                 	echo 'TestNG Report'
                 	 
                    	}
                     	step([$class : 'Publisher', reportFilenamePattern : '**/testng-results.xml'])   
                      	}
               	}*/
   
    
/* 	stage('Build Images') {
        	steps {

	git url:'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_be.git',branch:'developer', credentialsId: 'GitLab-SSH-sonali123'
                	sh 'mvn clean package'
            	script {
                	docker.withRegistry('docker-registry.cdacmumbai.in:5000') {
                    	def image = docker.build('docker-registry.cdacmumbai.in:5000/erp-admin-reimburse-be.jar')
        	}
      	}


        	git url: 'git@10.212.0.139:ecgc/smile/admin/erp_admin_reimb_fe.git',branch:'developer', credentialsId: 'GitLab-SSH-sonali123'
                	sh 'mvn clean package'
            	script {
                	docker.withRegistry('docker-registry.cdacmumbai.in:5000') {
                    	def image = docker.build('docker-registry.cdacmumbai.in:5000/erp-admin-reimburse-fe.jar')
        	}
      	}
 
    	}
	}*/
    
/*	stage('Containerization') {
        	steps {

           git url:'git@10.212.0.139:sonali123/bud-ci-cd.git',branch:'master',credentialsId: 'GitLab-SSH-sonali123'
            	sh "docker-compose up"
          	 
        	}
    	}*/
    
	/*stage('Security Testing') {
        	steps {
            	script {
                	// Proxy tests through ZAP
                	runZapCrawler(host: "http://10.212.0.72:8081/")
            	}
           	 
        	}
    	}*/

    
 /*	stage('Upload Images '){
         	steps{
      	withCredentials([string(credentialsId: 'DockerRegistryID', variable: 'DockerRegistryID')]) {
   
            	 
       	}

        	sh  "docker push $DOCKER_SERVER"
         	sh  " docker push $DOCKER_BE"
         	sh  "docker push $DOCKER_FE"

     	}      	 
 	}*/


    
}
post {
    	// Always runs. And it runs before any of the other post conditions.
    	always {
       	 
    	//ZAP Report
        /*	script {
            	archiveZap(failAllAlerts: 0, failHighAlerts: 0, failMediumAlerts: 0, failLowAlerts: 0)
        	}*/
  	 
        	// Let's wipe out the workspace before we finish!
         	cleanWs()
    	}
   	 
	}


}
