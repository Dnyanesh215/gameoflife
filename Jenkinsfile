pipeline{
	agent{
		label{
			label "slave-1"
			customWorkspace "/mnt/project"
		}
	}
	stages{
		stage("cloning repo and deleting maven local repo"){
			steps{
				sh "rm -rf *"
				sh "sudo rm -rf /root/.m2/repository"
				sh "git clone https://github.com/Dnyanesh215/gameoflife.git -b slave"
			}
		}
		stage("build and deploy on Apache Tomcat"){
			steps{
				dir ("/mnt/project/gameoflife/"){
					sh "mvn clean install -DskipsTest=TRUE"
					sh "cp /mnt/project/gameoflife/gameoflife-web/target/gameoflife.war /mnt/server/apache-tomcat-9.0.81/webapps"
				}
			}
		}
	}
}
