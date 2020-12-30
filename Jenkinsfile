pipeline {
    agent any 
    stages {
        stage('Sonarqube test11') { 
            environment { 
                scannerHome = tool 'SonarQubeScanner' 
            } 
            steps { 
                withSonarQubeEnv('sonarqube') { 
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=jacocodemo -Dsonar.sources=. -Dsonar.java.binaries=. " 
                } 
                timeout(time: 10, unit: 'MINUTES') { 
                    waitForQualityGate abortPipeline: true 
                } 
            } 
        } 
    }
}
