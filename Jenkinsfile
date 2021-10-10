pipeline{ 
    agent any 
    tools {
        maven 'Maven3.8'
        
      }
    stages{

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