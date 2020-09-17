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
      }
    stages{
      
	 stage('Pre build Notification')
         {
	     steps
             {
                 script{
                 
                echo "$env.GIT_URL"
		echo "$env.GIT_COMMIT"
                 echo "${BUILD_USER}"
	         echo "${GIT}"
                 }
                 }
                 }
                 }
                 }
