[200~node('master') 
{
    stage('ContinuousDownload')
    {
      git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
      sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
      sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.30.159:/var/lib/tomcat8/webapps/qaapp.war'
    }
    stage('ContinuousTesting')
    {
      git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
      sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
      sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.18.23:/var/lib/tomcat8/webapps/prodapp.war'
    }



}
