

pipeline {

    agent any

    environment {
    PATH = "/usr/local/bin/:${env.PATH}"
  }
    
 
    stages {
        stage('Docker Creds') {
            steps {
                echo '>>> Build Application .'
                echo "PATH is: ${env.PATH}"
            }
        }

        stage('Build Application') {
            steps {
                //sh "make build"
                //sh "make test"
                // no configuration to validate at the moment
                //sh "make vet"
                //sh "make package"
                echo '>>> Build Application .'
            }
        }
        stage('Publish Results') {
            steps {
                echo '>>> Publish Results'
            }
        }
        stage('Test Application') {
            steps {
                 echo 'Test Application'

            }
           
        }
     


        stage('Publish Schema') {
            steps {
                    echo '>>> Publish Schema'
                    echo "current build number: ${currentBuild.number}"
                    echo "previous build number: ${currentBuild.previousBuild.getNumber()}"


                    
                    //sh "aws s3 cp schema/aps-search-lambda.yaml s3://san-app/openAPI/${env.JOB_NAME}/${env.BUILD_NUMBER}/ --metadata '{\"san\":\"34533452\"}'"

                    sh "aws s3 cp schema/petstore.yaml s3://san-app/openAPI/${env.JOB_NAME}/${env.BUILD_NUMBER}/"
                    //sh "aws s3 cp schema/petstore.yaml s3://inception-artifactory/openAPI/${env.JOB_NAME}/latest/"
                    //sh "aws s3api put-object-tagging --bucket  inception-artifactory --key openAPI/${env.JOB_NAME}/${env.BUILD_NUMBER}/petstore.yaml --tagging '{\"TagSet\": [{\"Key\": \"client.platform\", \"Value\": \"aps atom\"},{\"Key\": \"build.version \", \"Value\": \"${currentBuild.number}\"}]}' "
                   
                    echo 'completed.'
            }
        }
        
           
          
       
    }

}
    


