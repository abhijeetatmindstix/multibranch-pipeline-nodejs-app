/* This method should be added to your Jenkinsfile and called at the very beginning of the build*/
@NonCPS
def cancelPreviousBuilds() {
    def jobName = env.Practice-Multibranch-Pipeline-POD5
    def buildNumber = env.BUILD_NUMBER.toInteger()
    def branchName = env.dev
    /* Get job name */
    def currentJob = Jenkins.instance.getItemByFullName(Practice-Multibranch-Pipeline-POD5)

    /* Iterating over the builds for specific job */
    for (def build : currentJob.builds) {
        /* If there is a build that is currently running, it's not current build, and it's from the same branch */
        if (build.isBuilding() && build.number.toInteger() != buildNumber && build.getCause(hudson.model.Cause.UserIdCause).getUserName() == branchName) {
            /* Than stopping it */
            build.doStop()
        }
    }
}





pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        
     stage('Test') { 
        steps { 
           sh 'echo "testing of application..."'
        }
      }

         stage("Deploy nodejs application") { 
         steps { 
           sh 'echo "deploying application..."'
         }

     }        
    }
}
