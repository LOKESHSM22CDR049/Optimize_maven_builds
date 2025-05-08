pipeline {
    agent any

    tools {
        maven 'Maven 3.9'
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', url: 'https://github.com/LOKESHSM22CDR049/Optimize_maven_builds'
            }
        }

        stage('Parallel Build') {
            parallel {
                core {
                    steps {
                        sh 'mvn -pl core clean install -am -T 2'
                    }
                }
                api {
                    steps {
                        sh 'mvn -pl api clean install -am -T 2'
                    }
                }
                service {
                    steps {
                        sh 'mvn -pl service clean install -am -T 2'
                    }
                }
                web {
                    steps {
                        sh 'mvn -pl web clean install -am -T 2'
                    }
                }
            }
        }

        stage('Verify') {
            steps {
                sh 'mvn verify'
            }
        }
    }
}
