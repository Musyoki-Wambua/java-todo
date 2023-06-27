pipeline {
    agent any
    
    tools {
        gradle "Gradle-6"
    }
    environment {
        VERSION_NUMBER = '1.6'
    }
    stages {
        stage('Clone Repository'){
            steps {
                git 'https://github.com/Musyoki-Wambua/java-todo'
            }
        }
        stage("Build Project"){
            steps{
                sh 'gradle build'
            }
        }
        stage("Tests") {
            steps{
                sh 'gradle test'
            }
        }
        stage('Deploy to Heroku') { 
            steps { 
                withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){ 
                    sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/intense-shelf-05741.git master'
                } 
                
            }
            
        } 
        
    }
}