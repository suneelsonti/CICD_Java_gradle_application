pipeline{
    agent any
    stages{
        stage("SCM_Checkout"){
            steps{
                echo "Checking out code from Git"

            }
        stage("Sonar Scan") {
            agent{
                docker{
                    iamge 'openjdk:11'
                }
            }
            steps{
                withSonarQubeEnv(credentialsId: 'sonartoken') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube'
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
}