def getBuildUser(){
    return wrap([$class: 'BuildUser']) { return env.BUILD_USER }
}

def gitCommitURL() {
    gitcommit=env.GIT_URL.replace('.git','')+"/commit/"+env.GIT_COMMIT   
    return gitcommit
}

pipeline
{
  agent any
  environment{
      BUILD_USER= getBuildUser()
     GIT=gitCommitURL()
build_url = "${env.BUILD_URL}"

      }
    stages{
      
	 stage('Pre build Notification')
         {
	     steps
             {
                 script{
                 
                echo "$env.GIT_URL"
		//echo "$env.GIT_COMMIT"
                 echo "${BUILD_USER}"
	         echo "${GIT}"
			 echo "${build_url}"
		/*def version_number = sh (script: "cat pom.xml",returnStdout: true).trim()
			 def version = sh (script: "cat pom.xml | grep -m 1 'version'",returnStdout: true).trim()
			 echo "$version_number"		     
			 echo "$version"*/
			 def version_number = sh (script: "cat pom.xml | grep -m 1 'version'",returnStdout: true).trim()
                     def version_1 = version_number.split('>')
                     Version = version_1[1].split('<')
                     Version =Version[0]                                          
		     echo "$Version"
			/* if("${Version}".contains("SNAPSHOT")){         
                      error('Build Fail Due to pom.xml not having version number')
 } */
                 }
                 }
                 }
                 }
	post{
	 always {
           jiraSendBuildInfo site: 'team-1625869429732.atlassian.net'
       }
                 }
}
