pipeline {
    agent any
    triggers{ pollSCM('*/1 * * * *') }

    stages {
// Būvējuma izveide        
        stage('install-pip-deps') {
            steps {
                script{
                    installPipDeps()
                }
            }
        }
    }
}

def installPipDeps(){
    echo "Installing all required depdendencies.."
}
