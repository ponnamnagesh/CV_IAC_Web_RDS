pipeline {
    agent any
    
    stages {
     
        stage('Checkout') {
            steps {
             //sh ('cd cv/${Environment}/${component}/')
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ponnamnagesh/CV_IAC_Web_RDS.git']]])            
              //git([url: 'git@github.com:ponnamnagesh/TerraformJenkinsS3Ansible.git', branch: 'main', credentialsId: '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'])
              //sh ('cd cv/${Environment}/${component}/')
          }
        }    
        stage ("Terraform Init") {
            steps {
                sh ('cd /var/lib/jenkins/workspace/CV_IAC_WEB_RDS/cv/${Environment}/${component}/')
                sh ('sudo terraform init') 
            }
        }
        stage ("Terraform Plan") {
            steps {
                sh ('terraform plan') 
            }
        }
        stage ("Terraform Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
                //sh ('terraform apply --auto-approve') 
                //sh ('terraform destroy --auto-approve')
           }
        }
    }
}
