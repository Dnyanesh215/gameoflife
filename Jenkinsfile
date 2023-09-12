pipeline{
	agent{
		label{
			label "built-in"
			customWorkspace "/mnt/project"
		}
	}
	stages{
		stage("clone and built and deploy"){
			steps{
				sh "rm -rf *"
				sh "git clone https://github.com/Dnyanesh215/gameoflife.git"
				dir("/mnt/project/game-of-life"){
					sh "mvn clean install -DskipTest=TRUE"
				}
				sh "cp /mnt/project/game-of-life/gameoflife-web/target/gameoflife.war /mnt/server/apache-tomcat-9.0.80/webapps"
			}
		}
	}
}
