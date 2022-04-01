pipeline
{
    agent any
    stages
    {
        stage('ContinousDownload-Credit Cards')
        {
            steps
            {
                script
                {
                     try
                    {
                        git 'https://github.com/ArkLearnersEdge/maven.git'
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'CD failed to download the code from git repo', cc: 'scrum_grp@gmail.com', from: '', replyTo: '', subject: 'It may fail at stage 1', to: 'scrumm1@gmail.com'
                    }
                }
            }
        }
         stage('ContinousBuild')
        {
            steps
            {
                script
                {
                     try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                       mail bcc: '', body: 'CI-CD fail at stage2 to build mvn package', cc: 'scrum_grp@gmail.com', from: '', replyTo: '', subject: 'it mayfail at stage 2', to: 'scrumm1_@gmail.com'
                    }
                }
            }
        }
         stage('ContinousDeploy')
        {
            steps
            {
                script
                {
                     try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/development/webapp/target/webapp.war ubuntu@172.31.16.236:/var/lib/tomcat8/webapps/testapps'
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'CI-CD fail at stage3 to deploy at tomcat8 code', cc: 'scrum_grp@gmail.com', from: '', replyTo: '', subject: 'it mayfail at stage 3', to: 'scrumm1_@gmail.com'
                    }
                }
            }
        }
         stage('ContinousTesting')
        {
            steps
            {
                script
                {
                     try
                    {
                        git 'https://github.com/ArkLearnersEdge/FunctionalTesting.git'
                        sh 'java -jar /home/ubuntu/.jenkins/workspace/development/testing.jar'
                    }
                    catch(Exception e4)
                    {
                       mail bcc: '', body: 'CI-CD fail at stage4 for testing ', cc: 'scrum_grp@gmail.com', from: '', replyTo: '', subject: 'it mayfail at stage 4', to: 'scrumm1_@gmail.com'
                    }
                }
            }
        }
        stage('ContinousDelivery')
        {
            steps
            {
                script
                {
                     try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/development/webapp/target/webapp.war ubuntu@172.31.31.120:/var/lib/tomcat8/webapps/prodapp'
                    }
                    catch(Exception e5)
                    {
                      mail bcc: '', body: 'In CI-CD at stage level the production of delivery is failed', cc: 'scrum_grp@gmail.com', from: '', replyTo: '', subject: 'In stage 5 Continuous Delivery failed', to: 'scrumm1_@gmail.com'
                    }
                }
            }
        }
    }
}
