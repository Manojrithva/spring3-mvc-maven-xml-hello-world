pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
              git credentialsId: '8dceaae1-062c-421b-a640-a48ea399e0e1', url: 'https://github.com/Manojrithva/spring3-mvc-maven-xml-hello-world.git'
            }
        }
        stage('Build') {
            steps {
                // maven packages
        sh "mvn -Dmaven.test.failure.ignore=true clean package"
    }
}
stage ('Artifacts') {
            steps {
                
                 archiveArtifacts 'target/*.war'
                }
           }
           
          stage('deploy') {
            steps {
                // Tomcat deploy
              withCredentials([usernameColonPassword(credentialsId: '94ca2537-06b4-430b-9547-82a0fa8d64bf' , variable: 'rithva')]) {sh "curl -v -u ${rithva} -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-3-6-87-142.ap-south-1.compute.amazonaws.com:8085/manager/text/deploy?path=/mahirithvamano&update=true'"  
              } 
         
        }
          }
    } 
}
