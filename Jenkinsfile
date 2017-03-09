pipeline {
    agent none

    stages {
        stage('build & unit tests') {
            agent { label 'build' }
            steps{
                sleep 5
            }
        }

        stage('static-analysis') {
            agent { label 'build' }
            steps {
                sleep 5
            }
        }

        stage('acceptance tests') {
            steps{
                parallel (
                    'chrome': {
                        node('build') {
                            sleep 5
                        }
                    },
                    'edge' : {
                        node('build') {
                            sleep 5
                        }
                    },
                    'firefox': {
                        node('build') {
                            sleep 5
                        }
                    }
                )
            }
        }

        stage('staging') {
            agent any
            steps {
                sleep 5
            }
        }

        stage('manual-approval') {
            steps {
                input 'Deploiement en production'
            }
        }

        stage('deploy') {
            agent any
            steps {
                sleep 5
            }
        }
    }
}
