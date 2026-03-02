node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=Group-Onee_Test1_0035ba2e-ab86-4a9c-aa9d-ec0115229620 -Dsonar.projectName='Test1'"
    }
  }
}
