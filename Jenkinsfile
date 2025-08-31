pipeline {
  agent any
  stages {
    stage('terraform-install') {
      steps {
        sh '''sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo yum -y install terraform'''
      }
    }

    stage('terraform-init') {
      steps {
        sh 'terraform init'
      }
    }

  }
}