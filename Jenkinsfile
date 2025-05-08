pipeline {
    agent any

    tools {
        maven 'Maven 3.9' // Define in Global Tool Config
    }

    environment {
        MAVEN_OPTS = "-Xmx1024m"
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', url: 'https://github.com/LOKESHSM22CDR049/Optimize_maven_builds'
            }
        }

        stage('Build Modules in Parallel') {
            parallel {
                moduleA {
                    steps {
                        sh 'mvn -pl module-a clean install'
                    }
                }
                moduleB {
                    steps {
                        sh 'mvn -pl module-b clean install'
                    }
                }
            }
        }

        stage('Aggregate') {
            steps {
                sh 'mvn verify'
            }
        }
    }
}
