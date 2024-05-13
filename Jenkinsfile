pipeline{

    agent any

    stages{

        stage("CONTINOUS DOWNLOAD"){

            steps{
                git branch: 'main', url: 'https://github.com/clemenrance/SIELI-CODE.git'
            }
        }
        stage("Unit Test"){

            steps{
                sh'mvn test'
            }
        }
        stage("Intergration Test"){

            steps{
                sh'mvn verify -DskipUnitTests'
            }
        }
        stage("Contionous Build"){

            steps{
              sh'mvn clean install'  
            }
        }
        stage("Static Test Analysis"){

            steps{

                script{
                    withSonarQubeEnv(credentialsId: 'Sonar-auth'){
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Continous Delivery"){

            steps{

                script{
                    sh 'cp -r /root/.jenkins/workspace/SIELI/ /var/www/html/'
                }
            }
        }
    }
}