pipeline
{ 
    agent any
    stages
    {
        stage("Execute Playbook"){
            steps{
                sh " sudo ansible-playbook /root/install-grafana.yml"
                
            }
            
        }
    }
}
