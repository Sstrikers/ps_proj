EMAIL='sergey_tsurankov@epam.com'
<<<<<<< HEAD
BRANCH='*/ps_pipeline'
=======
BRANCH='*/dev_pipeline'
>>>>>>> 467338685dcfaeed258f34873915a795dee1380e
GIT_URL='https://github.com/Sstrikers/ps_proj'
GIT_CREDENTIALS='c39d22e1-bb70-4f2b-980d-03abdc91361b'
pipeline {
    agent {
        node {
                label 'Windows12'
        }
    }
    triggers { pollSCM('*/1 * * * *') }
    stages {
        stage('Test'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: BRANCH]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: GIT_CREDENTIALS, url: GIT_URL]]])    
            }
            
        }
    }
    post{
        failure {
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
                to: EMAIL
            )
        }
    }
}    

