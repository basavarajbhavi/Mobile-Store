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
        stage('Run the Mvn Application'){
            steps{
                echo 'Running the Mvn Application'
                sh 'mvn spring-boot:start'
            }
            stage ('building the docker image'){
            steps{
                echo 'Docker image Build'
                sh'docker build -t aakashsrnvsn/mobilestore'
            }
        }
        stage('Deploy to dev'){
            steps{
                echo 'Deploying the dev environment'
                sh 'docker rm -f mobile || true'
                sh 'docker run -d --name=mobile -p 8081:8099 aakashsrnvsn/mobilestore:latest'
            }
        }
    }
}
