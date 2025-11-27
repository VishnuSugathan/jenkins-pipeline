pipeline {
    agent any

    environment {
        JMETER_HOME = 'C:\\Users\\Administrator\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3'
        REPO_URL = 'https://github.com/VishnuSugathan/jenkins-pipeline.git'
        JMX_FILE = 'jenkins-pipeline/Get_Request.jmx'
        REPORT_DIR = 'jmeter_reports'
        RESULT_FILE = 'result.jtl'
        HTML_REPORT_DIR = 'jmeter_reports\\html_report'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: "${REPO_URL}", branch: 'main'
            }
        }

        stage('Run JMeter Test') {
            steps {
                script {
                    // Create the report directories if they don't exist
                    bat "mkdir ${WORKSPACE}\\${REPORT_DIR}"
                    bat "mkdir ${WORKSPACE}\\${HTML_REPORT_DIR}"

                    // Run JMeter test with the output format set to CSV
                    bat """
                    "${JMETER_HOME}\\bin\\jmeter" -n -t "${JMX_FILE}" -l "${WORKSPACE}\\${REPORT_DIR}\\${RESULT_FILE}" -e -o "${WORKSPACE}\\${HTML_REPORT_DIR}" -Jjmeter.save.saveservice.output_format=csv
                    """
                }
            }
        }
    }

    post {
        always {
            cleanWs()  // Clean workspace after the run
        }
    }
}
