pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Jenkins Minute pipeline'
          }
        }

        stage('terraform-init') {
          steps {
            sh '''export TF_IN_AUTOMATION=true
terraform init
terraform plan -no-color'''
          }
        }

      }
    }

  }
}