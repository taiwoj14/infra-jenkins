pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
           git branch: 'main', url: 'https://github.com/ooghenekaro/infra-jenkins.git'
  
            }
        }
    
        stage ("terraform init") {
            steps {
                sh ("terraform init") 
            }
        }
        
        stage ("plan") {
            steps {
                sh ('terraform plan') 
            }
        }

        stage (" Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
           }
        }
    }
}
    
