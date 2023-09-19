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
        stage('Run the Mvn Applicatio'){
            steps{
                echo 'Running the Mvn Application'
                sh 'sudo mvn spring-boot:start'
            }
        }
    }
}
