pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scmGit(
    branches: [[name: 'master']],
    userRemoteConfigs: [[url: 'https://github.com/ahmedsalam007/contintiousApp.git']])
            }
        }
        
        stage('Install dependencies') {
            steps {
               bat 'npm i'
            }
        }
        
         stage('test by angular-cli') {
            steps {
               bat 'ng test --no-watch --no-progress --browsers=ChromeHeadless'
            }
        }
        
        stage('build') {
            steps {
               bat 'ng build'
            }
        }
        
        
        stage('move files to nginx') {
            steps {
               bat 'xcopy /e /y "./dist/contintious-app" "C:/Users/Ahmed_Abdelsalam/Downloads/nginx-1.24.0/nginx-1.24.0/html"'
               bat 'start chrome "http://localhost"'
            }
        }
    }
}