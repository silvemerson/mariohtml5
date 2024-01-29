pipeline{
    agent any
    stages{
        stage('Quality-Gate'){
            steps{
                script{
                    def scannerPath = tool "supermario-scanner"
                    withSonarQubeEnv('supermario-sonarqube'){
                        //sh "${scannerPath}/bin/sonar-scanner -Dsonar.projectKey=supermario -Dsonar.sources=./webapp"
                        sh "${scannerPath}/bin/sonar-scanner -Dsonar.projectKey=supermario -Dsonar.sources=./webapp -Dsonar.host.url=http://10.96.6.74 -Dsonar.token=sqp_beec16ed103b9154ab1baaec137b4187e52f7544"
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
