pipeline {
   agent any
   stages {
    stage('Checkout') {
      steps {
        script {
           git credentialsId: 'asvssa', url: 'https://github.com/asvssa/ansible-windows.git'
           // Checkout to a specific branch in your repo.
           sh "git checkout master"
          }
       }
    }
    stage('Update the ansbile Inventory') {
      steps {
        script {
          sh "mkdir -p /etc/ansible"
          sh "mv hosts /etc/ansible/"
        }
      }
    }
    stage('Run Ansible Playbook') {
      steps {
         script {
           sh "/usr/local/bin/ansible-playbook win_updates.yaml"
         }
      }
    }
   }
}
