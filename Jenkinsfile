pipeline {
    agent any

    stages {        
        stage('JF:Install dependencies') {
            steps {
               bat 'npm i'
            }
        }
        
         stage('JF:test by angular-cli') {
            steps {
               bat 'ng test --no-watch --no-progress --browsers=ChromeHeadless'
            }
        }
        
        stage('JF:build') {
            steps {
               bat 'ng build'
            }
        }
        
        
        stage('JF:move files to nginx') {
            steps {
               bat 'xcopy /e /y "./dist/contintious-app" "C:/Users/Ahmed_Abdelsalam/Downloads/nginx-1.24.0/nginx-1.24.0/html"'
               bat 'start chrome "http://localhost"'
            }
        }
    }
}