// pipeline {
//     agent any

//     environment {
//         PATH = "/opt/homebrew/bin:$PATH"
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'npm install'
//             }
//         }
        
//      stage('Test') { 
//         steps { 
//            sh 'echo "testing application..."'
//         }
//       }

//          stage("Deploy nodejs application") { 
//          steps { 
//            sh 'echo "deploying application..."'
//          }

//      }       
//    }
//   }




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
          
  }
  post {
    always {
      script {
        def previousBuild = currentBuild.previousBuild
        if (previousBuild != null) {
          def previousBuildUrl = previousBuild.getUrl() + "doAbort"
          def response = httpRequest url: previousBuildUrl, httpMode: "POST"
          if (response.status == 200) {
            echo "Previous build was successfully aborted"
          } else {
            echo "Failed to abort previous build: ${response.status} ${response.statusText}"
          }
        }
      }
    }
  }
}

