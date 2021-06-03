pipeline{
agent { label 'dev' }
stages{
stage('checkout'){
steps{
checkout([$class: 'GitSCM', 
    branches: [[name: '*/master']], 
    userRemoteConfigs: [[credentialsId: '0d56ebf8-1557-4503-9ffd-b835c0fef0c0', url: 'https://github.com/mywatsapp/mavenrepo.git']]
])


     }
   }
stage('build'){
steps{
sh "mvn package"
}
                    }
stage('sonar'){
steps{
withSonarQubeEnv('mysonarqube'){
sh "mvn sonar:sonar"
}
      }
   }
stage('deploy'){
steps{
sh "scp target/*.war 13.232.129.23:/var/lib/tomcat/webapps" 

}
}
  }
}

