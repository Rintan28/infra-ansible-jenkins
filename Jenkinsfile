pipeline {
    agent any
    environment {
        ANSIBLE_FORCE_COLOR = 'true'
    }
    stages {
        stage('Checkout Source') {
            steps {
                git branch: 'main', url: 'https://github.com/Rintan28/infra-ansible-jenkins.git'
            }
        }

        stage('Print Working Directory') {
            steps {
                sh 'pwd && ls -lah'
            }
        }
        
        stage('Run Ansible Playbook') {
            steps {
                sshagent(['ca12f8e2-13fd-46aa-ba90-89e549f3b8df']) {
                    sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i host.ini deploy.yml || exit 1'
                }
            }
        }
    }
}
