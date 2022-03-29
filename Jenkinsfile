pipeline {
 agent {
      kubernetes {
  label 'slave-dev'
            defaultContainer 'jnlp'
           yaml """
             apiVersion: v1
             kind: Pod
             metadata:
               labels: 
                 kube: slave-dev
             spec:
               containers:
               - name: jnlp
                 image: remony/jenkins-slave-base-centos7-ansible:v3.11
                 tty: true
                 securityContext:
                   privileged: true
              
             """
}//end of kubernetes
 }//end of agent


 
stages {
        stage('test-ansible'){
            steps{
                ansiblePlaybook credentialsId: 'root', installation: 'ansible', inventory: 'Inventory', playbook: 'Playbook.yml'
				}
										}

}//end of stages


}//end of pipeline
