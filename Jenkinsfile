pipeline {
    agent any
     environment {
            CI = 'true'
        }
    stages {
        stage('Build') {
            steps {
                tool(nodeJS:NodeJS-19.1.0){
                sh 'npm install'
                }
            }
        }
        stage('Test') {
                    steps {
                        sh './jenkins/scripts/test.sh'
                    }
                }
                stage('Deliver') {
                            steps {
                                sh './jenkins/scripts/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh './jenkins/scripts/kill.sh'
                            }
                        }

    }
}
