pipeline{
    agent any
    stages{
/*        stage("SCM_Checkout"){
            steps{
                echo "Checking out code from Git"

            }
        }  */   
        stage("Sonar Scan") {
            agent{
                docker{
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonartoken') {
                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube --warning-mode=all --stacktrace'
                    }
                }
            }
            
        }
            
    }
}
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
