import hudson.model.*

/*
@auhtor Aniket Kshirsagar

Jenkins library to cancel the current (older / unwanted) Jenkins builds in execution for the same Jenkins job while new commit is done and build with old code of no use as branch is in updated.

*/
void call(Map map = [:]) {
    
    // Get the name of the Jenkins job
    String currentJobName = env.JOB_NAME.concat("(.*)");

    // Get the number of the Current Jenkins build
    String buildNumber = env.BUILD_NUMBER.toInteger()

    // Get the list of builds which are in queue
    def queue = jenkins.model.Jenkins.getInstance().getQueue()
    def jobsInQueue = queue.getItems() 

    for ( i=0; i < jobsInQueue.length; i++ ){ 
        String tempQueueJobUrl = jobsInQueue[i].task.getUrl().replaceAll("job/","")
        println("Current Job: ${currentJobName}")
        println("Job In Queue: ${tempQueueJobUrl}")
        if(tempQueueJobUrl.matches(currentJobName)){  
            currentBuild.result = 'ABORTED'
            error("Current build #${buildNumber} is terminated as there are new builds in the queue")
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
           sh 'echo "testing application..."'
        }
      }

         stage("Deploy nodejs application") { 
         steps { 
           sh 'echo "deploying application..."'
         }

     }       
   }
  }



