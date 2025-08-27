pipeline {

    agent any

    stages{

        stage ("Test"){
            steps {
                sh 'mvn -v'
                sh 'mvn -f ./hello-app/pom.xml test'
            }
            post {
                always {
                    junit 'hello-app/target/surefire-reports/*.xml' 
                }
            }
        }

        stage ("Build"){
            steps{
                sh 'mvn -v'
                sh 'mvn -f ./hello-app/pom.xml -B -DskipTests clean package'
            }
            post {
                success{
                    echo "Now archiving the artifacts..."
                    arhiveArtifacts artifacts: '**/*.jar'
                }
            }
        }
    }
}

