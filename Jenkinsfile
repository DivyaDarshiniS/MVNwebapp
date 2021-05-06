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
bat "copy "C:\Users\User\.jenkins\workspace\mvnwebapp1\target\calculators.war" "C:\Program Files\Apache Software Foundation\Tomcat 9.0\webapps" "
}
stage('Start Tomcat Server'){
sleep(time:5,unit:"SECONDS")
bat "C:\Program Files\Apache Software Foundation\Tomcat 9.0\bin\startup.bat"
sleep(time:100,unit:"SECONDS")
}
}
}