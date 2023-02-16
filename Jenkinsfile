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
        stage('Sonarqube'){
            steps{
                echo 'Sonar Codequality'
                sh '''
                mvn clean verify sonar:sonar \
                    -Dsonar.projectKey=Mobilestore \
                    -Dsonar.host.url=http://172.174.142.7:9000 \
                    -Dsonar.login=sqp_b2528b6d7e51fffabd919f84ed3dc0a243c558b9
                    '''
            }
        } 
        stage ('buiding the docker image'){
             steps{
                echo 'Docker image Build'
                sh 'docker build -t mobilestore .'
        }
        }
        stage('Deploy to dev'){
            steps{
                echo "Deploying to dev environment"
                sh 'docker rm -f mobile || true'
                sh 'docker run -d --name=mobile -p 8099:8099 mobilestore'
            }
        }
    }
}