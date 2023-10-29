Assignment 4:
Create a Declarative CI pipeline for java based project that contains various stages like
Code checkout
Run below stages in parallel
- Code stability.
- Code quality analysis.
- Code coverage analysis.
Generate a report for code quality & analysis.
Publish artifacts.
Send Slack and Email notifications.
-----------------------------------------

    pipeline {
    agent any
    tools {
        maven 'mvn'
    }


    stage('Clone Repository') {
            steps {
                echo 'Started Cloning'
                git 'https://github.com/samirkesare/DevOpsCodeDemo.git'
            }
        }
        stage('Parallel Phase') {
            parallel {
                stage('Code Stability') {
                    steps {
                        echo "Testing code stability"
                        sh 'mvn test'
                    }
                }
                stage('Code Quality Analysis') {
                    steps {
                        echo "Check code quality using PMD"
                        sh 'mvn pmd:pmd'
                        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/pmd-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
                    }
                }
                stage('Code Coverage Analysis') {
                    steps {
                        echo "Check code coverage analysis using Jacoco"
                        sh 'mvn clean verify'
                        jacoco()
                    }
                }
            }
        }
        stage('Approval') {
            steps {
                input message: 'Do you want to proceed with publishing?', ok: 'Approve'
            }
        }
        stage('Publish Artifacts') {
            steps {
                echo 'Start to publish artifact'
                sh 'mvn package'
            }
        }

    
    post {
        success {
            script {
                emailext body: 'Job Succesfully Done', subject: 'Status of job', to: 'jenkinsnotificationtest250@gmail.com'
                slackSend channel: 'jenkins_notification6554', message: 'Job run successfully'
            }
        }
        failure {
            script {
                emailext body: 'Job failed', subject: 'Status of job', to: 'jenkinsnotificationtest250@gmail.com'
                slackSend channel: 'jenkins_notification6554', message: 'Job failed'
            }
        }
    }
    }

    
-------------------------------------------

<img width="945" alt="image" src="https://github.com/OT-MyGurukulam/Jenkins_Batch23/assets/98215406/5e57e535-d92e-408d-8a75-5a6b8399bcb0">

The user should have the option to skip various scans in the build execution. And before publish there should be an approval stage to be set in place to approve or deny the publish and if approved the step should execute and the user should be notified post successful/failed
Repeat the same using Scripted Pipeline.
