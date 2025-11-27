pipeline {
    agent any

    environment {
        // Define paths and files
        JMETER_HOME = 'C:\\Users\\Administrator\\Downloads\\apache-jmeter-5.6.3\\apache-jmeter-5.6.3'  // Update with your JMeter installation path
        REPO_URL = 'https://github.com/VishnuSugathan/jenkins-pipeline.git'
        JMX_FILE = 'jenkins-pipeline/Get_Request.jmx'  // Update path to match repository structure
        REPORT_DIR = 'jmeter_reports'  // Directory to store the reports
        RESULT_FILE = 'result.jtl'  // JMeter result file
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository to get the JMX file
                git url: "${REPO_URL}", branch: 'main'
            }
        }

        stage('Run JMeter Test') {
            steps {
                script {
                    // Ensure JMeter directory exists and run the test
                    bat """
                    "${JMETER_HOME}\\bin\\jmeter" -n -t "${WORKSPACE}\\${JMX_FILE}" -l "${WORKSPACE}\\${REPORT_DIR}\\${RESULT_FILE}" -e -o "${WORKSPACE}\\${REPORT_DIR}\\html_report"
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
