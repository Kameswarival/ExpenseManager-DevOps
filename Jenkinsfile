pipeline {
    agent {
        docker {
             image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2 -p 9191:8089'
        }

    stages {


    //Run PMD - The static code Analysis tool
    		stage('PMD') {
                steps {
                    sh 'mvn site'
                }
            }
    //End of PMD code

          }
      }
      }


/*

//Run Unit Test cases
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

//Run Jacoco - Code Coverage
		stage('Jacoco') {
            steps {
                sh 'mvn jacoco:report'
            }
        }



//Generate warfile
		stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
        }

//Run SonarCube - Static Analysis
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


//Run Artifactory
		stage('Artifactory') {
            steps {
                step([
				def server = Artifactory.server 'ART'
				server.publishBuildInfo buildInfo
				])
			}
        }

//Deplor war on Tomcat
	  stage('War deploy on Tomcat server') {
            steps {
				sh './jenkins/scripts/deliver.sh'
            }
        }


//Run System Test cases
		stage('System Test') {
            steps {
                sh 'mvn -Dtest=SystemTest1_Title.java'
            }
        }
    */
