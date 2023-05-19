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
// Būvējuma izvietošana “dev” vidē
        stage('deploy-to-dev') {
            steps {
                script{
                    deploy("dev", 7001)
                }
            }
        }
// Testu izpilde “dev” vidē
        stage('tests-on-dev') {
            steps {
                script{
                    test("dev")
                }
            }
        }
// Būvējuma izvietošana “staging” vidē
        stage('deploy-to-staging') {
            steps {
                script{
                    deploy("staging", 7002)
                }
            }
        }
// Testu izpilde “staging” vidē
        stage('tests-on-staging') {
            steps {
                script{
                    test("staging")
                }
            }
        }
// Būvējuma izvietošana “preprod” vidē
        stage('deploy-to-preprod') {
            steps {
                script{
                    deploy("preprod", 7003)
                }
            }
        }
// Testu izpilde “preprod” vidē
        stage('tests-on-preprod') {
            steps {
                script{
                    test("preprod")
                }
            }
        }
// Būvējuma izvietošana “prod” vidē
        stage('deploy-to-prod') {
            steps {
                script{
                    deploy("prod", 7004)
                }
            }
        }
// Testu izpilde “prod” vidē
        stage('tests-on-prod') {
            steps {
                script{
                    test("prod")
                }
            }
        }
    }
}

def installPipDeps(){
    echo "Installing all required depdendencies.."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    bat "dir"
    bat "pip install -r requirements.txt"
}

def deploy(String environment, int port){
    echo "Deployment to ${environment} has started.."
    git branch: 'main', poll: false, url: 'https://github.com/mtararujs/python-greetings'
    bat "pm2 delete greetings-app-${environment} & set \"errorlevel=0\""
}

def test(String environment){
    echo "Testing on ${environment} has started.."
}