pipeline {
  agent any
    
  stages {
     
                  stage('CleanWorkspace') {
            steps {
                cleanWs()
            }
        }
                                
                                
                stage("Code Checkout"){
            steps {
                script {
                                                                
                    sh "git clone https://github.com/ankusharma1988/jenkins-pipeline.git"
                   
                    
                }
            }
        }      
                                
                                
                                
    stage("Build Step"){
            steps {
                script {
                                                                
                    sh "cd $workspace"; sh "cp -rp $workspace/jenkins-pipeline/* $workspace";
                    sh "pwd"
                    sh "ls -lhrt ";
                    sh "mvn -version  ";
                    sh "mvn clean install"
                   
                    
                }
            }
        }
                stage(" Build Image"){
            steps {
                script {
                                                                
                    sh "cd $workspace";
                    sh "docker build -t java:v1.0 ."
                      
                }
            }
        } 
        
        
                                 stage(" Deploy Image"){
            steps {
                script {
			sh "docker kill jenkins-pipeline"
                        sh "docker container rm jenkins-pipeline"
			sh "docker run -dit --name jenkins-pipeline -p 8085:8085 java:v1.0"
                      
                }
            }
        }
                                
                stage(" verify Deployment"){
            steps {
                script {

                                                                                sh "docker ps "
                      
                }
            }
        }
  
  
  
  }

}
	
