pipeline {
    agent any
    tools {
        // Ensure these names match your "Global Tool Configuration" names
        maven 'Maven' 
        jdk 'JDK17' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // 'SonarQube-Local' must match the name in Jenkins > System
                withSonarQubeEnv('SonarQube-Local') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
