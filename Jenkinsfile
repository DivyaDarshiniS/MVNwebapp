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
			// publish html
        
			}
		}
		post {
        success {
          // publish html
          publishHTML target: [
              allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'coverage',
              reportFiles: 'index.html',
              reportName: 'RCov Report'
            ]
        }
		
	}
	stage('Install stage'){
		steps{
			withMaven(maven : 'apache-maven-3.8.1'){
			bat 'mvn install'
			}
		}
	}
stage('deploy to Tomcat'){
steps{

deploy adapters: [tomcat9(credentialsId: '7ca12bd3-9274-4ad3-9b1f-9b30847bb96e', path: '', url: 'http://localhost:8090/')], contextPath: 'calculators', war: '**/*.war'
}
}
}
}