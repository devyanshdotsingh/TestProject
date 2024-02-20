pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from your Git repository
                git branch: 'main', url: 'https://github.com/devyanshdotsingh/TestProject.git'
            }
        }
        
        // stage('SonarQube Analysis') {
        //     steps {
        //         // Perform SonarQube analysis
        //         // Adjust the properties as per your SonarQube setup
        //         script {
        //             def scannerHome = tool 'sonarqube_scanner'
        //             withSonarQubeEnv('SonarQube') {
        //                 sh "${scannerHome}/bin/sonar-scanner"
        //             }
        //         }
        //     }
        // }

        stage('OWASP Scan') {
            steps {
                // Perform OWASP scan
                // Add your OWASP scan commands here
            }
        }

        stage('Build Docker Image') {
            steps {
                 dir('backend') {
                    // Deploy
                    sh 'docker-compose up -d'
                }
            }
        }

    }
    
    // post {
        
    //     success {
    //         'Success'
    //     }
    //     failure {
    //         'Failed'
    //     }
    // }
}
