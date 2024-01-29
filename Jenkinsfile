pipeline{
    agent any
    stages{
        stage('Quality-Gate'){
            steps{
                script{
                    def scannerPath = tool "supermario-scanner"
                    withSonarQubeEnv('supermario-sonarqube'){
                        sh "${scannerPath}/bin/sonar-scanner -Dsonar.projectKey=supermario -Dsonar.sources=./webapp"
                    }
                }
            }
        }
        stage('SonarQube Analysis Result'){
            steps{
                timeout(time:30, unit: 'SECONDS'){
                    waitForQualityGate abortPipeline: false
                }
            }
        }
      }
}
