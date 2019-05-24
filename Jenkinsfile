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
              }

      }
      }
