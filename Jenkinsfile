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
}
