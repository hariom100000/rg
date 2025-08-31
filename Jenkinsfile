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

    stage('azure-cli -install') {
      steps {
        sh '''sudo dnf install -y https://packages.microsoft.com/config/rhel/8/packages-microsoft-prod.rpm
sudo dnf install azure-cli-2.44.1-1.el8 -y
az version'''
      }
    }

    stage('terraform-init') {
      steps {
        sh 'terraform init'
      }
    }

    stage('terraform-plan') {
      steps {
        sh 'terraform plan'
      }
    }

  }
  environment {
    AZURE_CREDS = 'serviceprincipal'
  }
}