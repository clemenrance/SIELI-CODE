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
    }
}