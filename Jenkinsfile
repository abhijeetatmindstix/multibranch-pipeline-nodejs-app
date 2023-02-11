pipeline {
    agent any
    options {
        disableConcurrentBuilds(abortPrevious: true)
    }
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
        stage("Cancel Older Builds") {
            steps {
                timeout(time: 10, unit: 'MINUTES') {
                    input message: "does this look good"
                }
            }
        }
      }
         
    } 










// pipeline {
//     agent any
//         options {
//                    disableConcurrentBuilds(abortPrevious: true)
//                 }
//     stages {
//         stage("cancel-previous-build") {
//             steps {
//                 cancelUnwantedBuilds()
//             }
//         }
//         stage("Cancel Older Builds") {
//             steps {
//                 timeout(time: 10, unit: 'MINUTES') {
//                     input message: "does this look good"
//                 }
//             }
//         }

//     }
    
// }
