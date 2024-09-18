pipeline {
  agent none

  stages {
    stage('Sonar Scanner') {
      agent { label 'sonar' }
      steps {
        withSonarQubeEnv('sonardemo') {
          sh '''
            mvn clean verify sonar:sonar \
            -Dsonar.projectKey=sonardemo \
            -Dsonar.projectName=sonardemo \
            -Dsonar.host.url=http://43.205.243.75:9000 \
            -Dsonar.login=sqp_ce20fed25983daa1bff9c9c306de0a4075d08837
          '''
          echo "Sonar scan successfully completed"
        }
      }
    }
    
    stage('Build Stage') {
      agent { label 'sonar' }
      steps {
        sh 'mvn clean install'
      }
    }
  }
}
