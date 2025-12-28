pipeline {
  agent any

  parameters {
    string(
      name: 'TARGET_IP',
      defaultValue: '10.128.0.5',
      description: 'IP of server to bootstrap'
    )
  }

  stages {
    stage('Run Ansible') {
      steps {
        sh """
        ansible-playbook playbooks/roles.yml \
          --limit ${TARGET_IP}
        """
      }
    }
  }
}
