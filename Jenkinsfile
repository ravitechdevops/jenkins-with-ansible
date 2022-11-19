pipeline {
  agent { 
  label 'ansible-node'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-user-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
        git branch: 'master', credentialsId: '919b152b-9b55-46c5-91ad-41b62ee996f7', url: 'https://github.com/ravitechdevops/jenkins-with-ansible.git'
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
