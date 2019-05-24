pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2 -p 9191:8089'
        }
    }
    stages {
		
		/*
        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }
		*/
		

		stage('PMD') {
            steps {
                sh 'mvn site'
            }
        }
	
		
        stage('UnitTest') {
            steps {
                sh 'mvn test'
            }	
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

/*
		
				stage('Jacoco Code Coverage') {
			steps {
				step([$class: 'JacocoPub', 
				execPattern: 'target/*.exec',
				classPattern: 'target/classes',
				sourcePattern: 'src/main/java',
				exclusionPattern: 'src/test*'
					])
				}
		}	
*/


		
		
		stage('Jacoco') {
            steps {
                sh 'mvn jacoco:report'
            }
        }

			
			
			
		stage('Build') {
            steps {
                sh 'mvn install'
            }
        }
		
/*
		stage('Static Code Analysis') {
            steps {
			 script {
          scannerHome = tool 'sonar-scanner'
        }
				withSonarQubeEnv('My SonarQube Server')
				{
				sh "${scannerHome}/bin/sonar-scanner"
				}
			}
		}
*/

		
		/*
		stage('Artifactory') {
            steps {
                step([
				def server = Artifactory.server 'ART'
				server.publishBuildInfo buildInfo
				])
			}
        }
		*/
		
      
	  stage('War deploy on Tomcat server') {
            steps {
				sh './jenkins/scripts/deliver.sh'
            }
        }
	
	  stage('Background process done') {
            steps {
				echo "Deployment on Tomcat WebServer Done"
            }
        }

		
/*		
		stage('System Test') {
            steps {
                sh 'mvn -Dtest=SystemTest1_Title.java'
            }
        }
*/		
		
    }

}