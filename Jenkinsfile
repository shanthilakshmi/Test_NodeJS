pipeline {
    agent any
    tools {nodejs 'NodeJS-16.18.1'}
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
                stage('Test') {
                    steps {
                        sh 'chmod +x -R Test_NodeJS'
                        sh 'rm -rf /var/lib/jenkins/.npm/_logs'
                        sh 'npm test'
                    }
                }
                stage('Deliver') {
                            steps {
                                
                                sh './Test_NodeJS/jenkins/scripts/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh './Test_NodeJS/jenkins/scripts/kill.sh'
                                //sh 'npm publish'
                            }
                        }

    }
}
