pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run JMeter Test') {
            steps {
                sh '''
                mkdir -p reports
                jmeter -n -t jmeter-tests/JPetStoreLogin.jmx -l reports/results.jtl -e -o reports/html
                '''
            }
        }

        stage('Archive Results') {
            steps {
                archiveArtifacts artifacts: 'reports/**', fingerprint: true
            }
        }
    }
}
