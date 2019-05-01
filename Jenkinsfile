properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        git 'https://github.com/cliftonhchang/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Test'){
        sh "ant -f test.xml -v"
        junit 'reports/*.xml'
    }
    
    stage('Deploy'){
        sh "aws s3 cp rectangle-" += System.getenv('JOB_NAME') += ".jar" s3://s3-seis665-cliftonhchang-hw10/"
    }       
    
    stage('Reports'){
//        aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins
        
    }
}
