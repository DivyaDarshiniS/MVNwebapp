pipeline{  
agent any
stages{
	stage('Compile Stage'){
		steps{
			withMaven(maven : 'apache-maven-3.8.1'){
			bat 'mvn clean compile'
			}
		}
	}
	stage('Testing Stage'){
		steps{
			withMaven(maven : 'apache-maven-3.8.1'){
			bat 'mvn test'
			}
		}
	}
	stage('Install stage'){
		steps{
			withMaven(maven : 'apache-maven-3.8.1'){
			bat 'mvn install'
			}
		}
	}
stage('Deploy to Tomcat'){
deploy adapters: [tomcat9(credentialsId: '86acd34d-afe3-4aa3-bc05-410aecd40860', path: '', url: 'http://localhost:8090/')], contextPath: 'calculators', war: '**/*.war'
}
stage('Start Tomcat Server'){
sleep(time:5,unit:"SECONDS")
bat "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\bin\\startup.bat"
sleep(time:100,unit:"SECONDS")
}
}
}