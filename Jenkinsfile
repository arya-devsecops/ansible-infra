pipeline {
    agent { label "${AGENT_LABEL}" }

    parameters {
        choice(
            name: 'AGENT_LABEL',
            choices: [
                'agent-2',
                'agent-1'
            ],
            description: 'Select Jenkins agent to run the job'
        )

        string(
            name: 'TARGET_IP',
            defaultValue: '10.128.0.5',
            description: 'Target server IP'
        )
    }

    stages {
        stage('Verify Agent') {
            steps {
                sh '''
                echo "Running on agent:"
                hostname
                whoami
                '''
            }
        }

        stage('Run Ansible') {
            steps {
                sh '''#!/bin/bash
                set -e
                which ansible-playbook || true
                /usr/bin/ansible-playbook playbooks/roles.yml \
                  --limit ${TARGET_IP}
                '''
            }
        }
    }
}
