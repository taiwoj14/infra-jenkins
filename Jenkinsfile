pipeline {
    agent any
    
    environment {
      ACCESS_KEY = credentials('karo-ecr')
        SECRET_KEY = credentials('karo-ecr')
    }

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
                sh ('terraform plan -var access_key=$ACCESS_KEY -var secret_key=$SECRET_KEY') 
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
    
