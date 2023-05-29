pipeline {
    agent any
    
    environment {
         ACCESS_KEY = credentials('AWS_ACCESS_KEY_ID')
        SECRET_KEY = credentials('AWS_SECRET_ACCESS_KEY')
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
                sh ("terraform plan -var 'ACCESS_KEY=AWS_ACCESS_KEY_ID' -var 'SECRET_KEY=AWS_SECRET_ACCESS_KEY' ") 
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
    
