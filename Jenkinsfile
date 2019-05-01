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
        a='rectangle-'
        b=System.getenv('BUILD_NUMBER')
        c= ".jar s3://s3-seis665-cliftonhchang-hw10/"
        c="$a$b$c"
        sh "aws cp $a$b$c" 
    }       
    
    stage('Reports'){
//        aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins
        
    }
}
