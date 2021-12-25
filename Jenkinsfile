pipeline {
    agent any
    
    stages {
        
        stage ('Initialization') {
            steps {
                sh 'echo "Starting the CI pipeline."'
            }
        }
        
        stage ('Build') {
            steps {
                sh 'npm install'
            }
        }
        
        stage ('NPM Audit Analysis') {
            steps {
                sh '/var/tmp/npm-audit.sh'
            }
        }
        
        stage ('NodeJsScan Analysis') {
            steps {
                sh 'nodejsscan --directory `pwd` --output /var/jenkins_home/workspace/node-app-pipeline/reports/nodejsscan-report'
            }
        }
        
        stage ('Retire.js Analysis') {
            steps {
                sh 'retire --path `pwd` --outputformat json --outputpath /var/jenkins_home/workspace/node-app-pipeline/reports/retirejs-report --exitwith 0'
            }
        }
        
        stage ('Dependency-Check Analysis') {
            steps {
                sh '/var/tmp/dependency-check/bin/dependency-check.sh --scan `pwd` --format JSON --out /var/jenkins_home/workspace/node-app-pipeline/reports/dependency-check-report --prettyPrint'
            }
        }
                
    }
}
