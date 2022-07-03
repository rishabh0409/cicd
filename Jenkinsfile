pipeline{
    agent any
    
    stages{
        stage("Pull the code "){
            steps{
                 git 'https://github.com/rishabh0409/cicd.git'
            }
        }
        stage("Building the code "){
            steps{
                sh 'mvn clean package install '
            }
        }
         stage('docker build image') {
            steps {
               
               sh 'docker build -t rishabh0409/cicd:${BUILD_ID}  .'
              }
        }
         stage('docker images push ') {
            steps {
                 
               sh 'docker push rishabh0409/cicd:${BUILD_ID} '
                 }            
            }     
         stage('kubernetes test ') {
            steps {
               
               sh 'helm upgrade cicd    --set image.repository=rishabh0409/cicd:${BUILD_ID} chart/.'  
           }  
        }   
        
    }
}
