pipeline{
  agent none
  stages {
    stage ("sonar scanner") {
      agent {label 'sonar'}
      steps{
        withSonarQubeEnv('sonardemo'){
          sh 'mvn clean verify sonar:sonar',
             '-Dsonar.projectKey=sonardemo',
             '-Dsonar.projectName='sonardemo'', 
             '-Dsonar.host.url=http://43.205.243.75:9000' ,
             '-Dsonar.token=sqp_ce20fed25983daa1bff9c9c306de0a4075d08837'
           echo "sonar scan successfully completed"
        }
        }
      }
      stage ('build stage'){
        agent {label 'sonar'}
        steps{
          sh 'mvn clean install'
        }
      }
  }
}
