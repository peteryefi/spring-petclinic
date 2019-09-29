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
                sh 'mvn -B -DskipTests clean package sonar:sonar -Dsonar.branch.name=master -Dsonar.host.url=http://192.168.10.100:900 -Dsonar.login=49295606ab4ecd6c45f735d04afe6f8012f0b2c8'
              }
            }
         }
    }
}
