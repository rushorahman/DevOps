pipeline
{
	agent any
	stages
	{
		stage('Checkout')
		{
			steps
			{
				git 'https://github.com/rushorahman/addressbook.git'
			}
		}
		
		stage('Build')
		{
			steps
			{
				dir('')
				{
					sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/MVN_HOME/bin/mvn package'
				}
			}
		}
		
		stage('Deployment')
		{
			steps
			{
				script
				{
					echo "Deployment"
					sh 'sudo cp /var/lib/jenkins/workspace/addressbook/target/addressbook.war /usr/share/tomcat/webapps/'
				}
			}
		}
	}
		
}
