pipeline{
    agent any
    tools{
        maven 'maven3.9.16'
    }
    
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['TESTING', 'PRODUCTION', 'DEVELOPMENT'],
            description: 'Select environment'
        )
    }
    stages{
        stage('git clone'){
            steps{
                git branch: 'main', credentialsId: 'jenkins-ci-cd', url: 'https://github.com/Shriharini1809/jenkins-ci-cd.git'
            }
        }
        stage('list'){
            steps{
                bat 'echo %PATH%'
            }
        }
        
        stage('maven test stage'){
            when{
                expression{
                    params.ENVIRONMENT == 'TESTING'
                }
            }
            steps{
                bat 'mvn test'
            }
        }
        stage('maven build stage'){
            steps{
                bat 'mvn clean package'
            }
        }
    }
}
