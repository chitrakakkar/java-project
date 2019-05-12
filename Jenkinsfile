node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/chitrakakkar/java-project.git'
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    stage('Build'){
        git 'https://github.com/chitrakakkar/java-project.git'
        sh "ant -f build.xml -v"
    }
    stage('Deploy'){
        sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${env.BUILD_NUMBER}.jar s3://hw10-jenkinsfile"   
    }
    stage('Reports'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '4f67c730-554d-449d-bdf8-5cfd3385dfa1', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
            sh 'aws cloudformation describe-stack-resources --stack-name jenkins-stack --region us-east-1' 
       }
    }
}
