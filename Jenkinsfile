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

    stage('az-login') {
      steps {
        sh '''
AZURE_CLIENT_ID=\'70f1443e-39c2-4d41-bb25-fb53bf2f66d8\'
AZURE_CLIENT_SECRET=\'16I8Q~mczScDfgTmyjbfi0pasuOPyHvuu~1X_aE9\'
AZURE_TENANT_ID=\'e89b9cb6-ceb6-41ac-8dcc-950ebbc47dae\'

az login --service-principal \\
            --username "$AZURE_CLIENT_ID" \\
            --password "$AZURE_CLIENT_SECRET" \\
            --tenant "$AZURE_TENANT_ID"'''
      }
    }

  }
  environment {
    AZURE_CREDENTIALS = 'credentials(\'serviceprincipal\')'
  }
}