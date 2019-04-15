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



  
   
 	stage('docker crear contenedor'){
            steps{
                sh 'docker run -d -p9090:8090 --name calculadora localhost:5000/calculadora'
            }  
     }        
        
    }
}
