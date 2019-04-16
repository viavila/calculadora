pipeline{
    agent any
    stages {
        stage('compilar'){
            steps{
                sh './gradlew compileJava'
            }
        }    
        stage('test'){
            steps{
                sh './gradlew test'
            }
     }
 	stage('contruir'){
            steps{
                sh './gradlew build'
            }  
     }        
 	stage('docker build'){
            steps{
                sh 'docker build -t localhost:5000/calculadora .'
            }  
     }         
 	stage('docker push '){
            steps{
                sh 'docker push localhost:5000/calculadora'
            }  
     }        

	stage("borrar contenedor") {

            when {

                expression { sh script: '''if [ -z $(docker ps -a -f name=calculadora -q) ]; then true; else false; fi''', returnStatus: true

                  }

              }

            steps {

                sh "sudo docker stop calculadora"

                sh "sudo docker rm calculadora"

             }

        }
   
 	stage('docker crear contenedor'){
            steps{
                sh 'docker run -d -p9090:8090 --name calculadora localhost:5000/calculadora'
            }  
     }        
        
    }
}
