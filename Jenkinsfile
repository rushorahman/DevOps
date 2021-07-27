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
		
		stage('Compile')
		{
			steps
			{
				dir('')
				{
					sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/MVN_HOME/bin/mvn compile'
				}
			}
		}
		
		stage('Test')
		{
			steps
			{
				dir('')
				{
					sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/MVN_HOME/bin/mvn test'
				}
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
					sh 'sudo cp /var/lib/jenkins/workspace/addressbookpackage/target/addressbook.war /usr/share/tomcat/webapps
                                        sh 'sudo rm -rf /usr/share/tomcat/webapps/addressbook'
                                        sh 'sudo systemctl restart tomcat'
				}
			}
		}
	}
		
}
