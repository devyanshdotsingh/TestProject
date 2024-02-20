pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from your Git repository
                git branch: 'main', changelog: false, credentialsId: 'CI_ssh', poll: false, url: 'git@github.com:devyanshdotsingh/TestProject.git'
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

        // stage('OWASP Scan') {
        //     steps {
        //         // Perform OWASP scan
        //         // Add your OWASP scan commands here
        //     }
        // }

        stage('Install Docker') {
            steps {
                script {
                    sh "echo admin | sudo -S apt-get update && sudo apt-get install -y docker-ce"
                }
            }
        }


        stage('Build Docker Image') {
            agent {
                node {
                    label "Agent_131u"
                }
            }
            steps {
                 dir('backend') {
                    // Deploy
                    sh 'docker-compose up d'
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
