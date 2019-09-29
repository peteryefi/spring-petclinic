pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage("build & SonarQube analysis") {
            steps {
              withSonarQubeEnv('SonarQube') {
                sh 'mvn -B -DskipTests clean package sonar:sonar -Dsonar.branch.name=master -Dsonar.host.url=http://192.168.10.100:900 -Dsonar.login=78f498970956a81d74dc7c157ba20be303bf220e'
              }
            }
         }
    }
}
