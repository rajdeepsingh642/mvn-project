pipeline {
    agent any
    tools{
        jdk "jdk11"
        maven "maven3"
    }

   stages {
        stage('git checkout') {
            steps {
                git branch: 'master', url:https://github.com/rajdeepsingh642/mvn-project.git 
            }
        }
        stage('compile') {
            steps {
             sh "mvn compile"
             }
        }    
       
        stage('build') {
            steps {
             sh "mvn package -DskipTests"
            }
        }

        stage('tomcat') {
            steps {
            sshagent(['tomcat-server']) {
              sh "scp -o strictHostKeycheking=no target/demo-maven.war tomcat@192.168.109.80:/opt/tomcat/webapps"
                    }
          
            }
        }    
   }


   
}