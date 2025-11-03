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
               credentialsId: 'c8d87dca-b36a-45e1-a548-795ca6647ed6', url: 'https://github.com/devesh-singhal/APIAutomationLearning'
             
            }
        }

        stage('Pull docker image') {
               steps {
                sh 'docker pull singhalfalcon/gorestddtest:1.0'
             
            }
        } 
    
         stage('Run API postman collection') {
               steps {
                sh 'docker run -v %cd%/newman:/app/results singhalfalcon/gorestddtest:1.0'
             
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