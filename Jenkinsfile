pipeline{ 
    agent any 
    tools {
        maven 'Maven3.8'
        
      }
    stages{

        stage ("Build"){
            steps{

                sh "mvn -B -DskipTests clean package"
            }
            }


        /*stage ("sonar scanning") {
            steps {
                script {
                    def scannerHome = tool name: 'mySonarScanner';
                    withSonarQubeEnv("mySonarqubeServer") {
                        sh "${tool("mySonarScanner")}/bin/sonar-scanner \
                        -Dsonar.projectKey=SimpleMaven \
                        -Dsonar.sources=. \
                        -Dsonar.java.binaries=target \
                        -Dsonar.host.url=http://44.197.132.246:9000/ \
                        -Dsonar.login=12e2853ff7e7d0dd75ce2666eca6699aa3dc6d0a"
                    }
               }
            }
        }*/

/*  created by Prasanth   */
        stage ("Ansible") {
            steps {
                 ansible-playbook local_host_ping.yml
               }
            }
        
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}