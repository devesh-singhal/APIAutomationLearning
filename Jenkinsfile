pipeline {
    agent any 
    stages {
        stage('build') {
               steps {
                echo 'building the war'
              
            }
        }
        stage('Deploy to QA') {
              steps {
                echo 'QA deployment done'
              }
            }
           
        stage('Git checkout') {
               steps {
              git branch: 'master', credentialsId: '6d73546b-07e2-4da1-9ac5-308c7e8e1468', url: 'https://github.com/devesh-singhal/APIAutomationLearning.git'
             
            }
        }

        stage('Pull docker image') {
               steps {
                bat 'docker pull singhalfalcon/gorestddtest:1.0'
             
            }
        } 
    
         stage('Run API postman collection') {
               steps {
                bat 'docker run -v %cd%/newman:/app/results singhalfalcon/gorestddtest:1.0'
             
            }
        } 

          stage('Publish HTML extra Report') {
               steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,              
                    reportDir: 'newman',
                    reportFiles: 'deveshsinghal.html',
                   reportName: 'HTML API POSTMAN COLLECTION EXECUTION REPORT',
                   reportTitles: '',
              ])
             
               }
               
          }
        

         stage('Deploy to PRODUCTION Env') {
               steps {
                echo 'Production Launch'
             
            }
        } 


    }
}  