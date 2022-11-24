pipeline {
    agent any
    tools {nodejs 'NodeJS-16.18.1'}
    stages {
        stage('clonig the repo'){
            steps{
                sh 'rm -rf Test_NodeJS'
                sh 'git clone https://github.com/shanthilakshmi/Test_NodeJS.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('run') {
                    steps {
                        sh 'npm run'
                        //sh "chmod +x -R Test_NodeJS"
                        //sh './Test_NodeJS/jenkins/scripts/test.sh'
                    }
                }
                stage('Test') {
                    steps {
                        sh 'chmod +x -R Test_NodeJS'
                        sh 'rm -rf /var/lib/jenkins/.npm/_logs'
                        sh 'npm install object.assign'
                        sh 'npm test'
                    }
                }
                stage('Deliver') {
                            steps {
                                sh './Test_NodeJS/jenkins/scripts/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh './Test_NodeJS/jenkins/scripts/kill.sh'
                            }
                        }

    }
}
