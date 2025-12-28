pipeline {
  agent any

  parameters {
    string(
      name: 'TARGET_IP',
      defaultValue: '10.128.0.5',
      description: 'IP of server to bootstrap'
    )
  }

    stage('Run Ansible') {
        steps {
            sh '''#!/bin/bash
            set -e
            /usr/bin/ansible-playbook roles.yml \
            --limit ${TARGET_IP}
            '''
        }
    }

}
