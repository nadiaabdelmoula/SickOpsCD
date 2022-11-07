pipeline
{
   agent any
    stages {
     stage('Pull') {
      steps{
       script{
     checkout([$class: 'GitSCM', branches: [[name: '*/master']],
         userRemoteConfigs: [[
         credentialsId: 'b728b8af-1534-449e-8abe-5ed9c7e78d1b',
         url:'https://github.com/nadiaabdelmoula/SickOpsCD.git']]])
         
         }
         }
         }
         stage('Build')
  {
             steps {
               script{
       sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                        }}}
                        
                        
          stage('docker') {
                  steps {
                   script{
     sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"

}}}

stage('docker-registry'){
            steps{
                script{
sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                }
            }
        }

         }
         }

