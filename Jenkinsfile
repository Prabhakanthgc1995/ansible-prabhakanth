pipeline {
    agent { label 'dev' }  // Specify the agent with the label 'dev'
      stages {
        stage('Checkout Code') {
            steps {
                // Checkout your repository that contains the Ansible playbook and roles
                checkout scm
            }
        }

        stage('Install Grafana with Ansible') {
            steps {
                script {
                    // Running the Ansible playbook to install Grafana
                    sh 'sudo ansible-playbook /root/install-grafana.yml'
                }
            }
        }

        stage('Verify Grafana Installation') {
            steps {
                script {
                    // Check if Grafana is running, for example, by querying its service
                    sh 'systemctl status grafana-server'
                }
            }
        }
    }

    post {
        always {
            // Cleanup steps, if needed
            echo 'Pipeline finished'
        }
        success {
            // Steps to execute if the pipeline was successful
            echo 'Grafana installation was successful!'
        }
        failure {
            // Steps to execute if the pipeline failed
            echo 'Something went wrong with the Grafana installation.'
        }
    }
}
