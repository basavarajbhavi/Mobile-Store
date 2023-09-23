pipeline{
    agent any
    stages{
        stage ('checkout the code from SCM'){
            steps{
                echo 'checkout the code'
            }
        }
        stage ('Build the project'){
            steps{
                echo 'building the project'
                sh 'mvn clean install -DskipTests'
            }
        } 
        stage ('buiding the docker image'){
             steps{
            echo 'Docker image Build'
            sh 'docker build -t skillassure/ibhmobilestore .'
        }
        }
        stage('Deploy to dev'){
            steps{
                echo "Deploying to dev environment"
                sh 'docker rm -f mobile || true'
                sh 'docker run -d --name=mobile -p 8081:8099 skillassure/ibhmobilestore:latest'
            }
        }

    }
}
