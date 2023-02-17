pipeline
{
   agent any
   stages
   {
     stage('contionuesDownload')
     {
       steps
       {
         git 'https://github.com/Vijay01234/maven.git'  
       }    
     }
     stage('contionuesbuild')
     {
       steps
       {
         sh 'mvn package'  
       }    
     }
     stage('contionuesdeployment')
     {
       steps
       {
         deploy adapters: [tomcat9(credentialsId: '66274cc8-505c-4de7-a8da-467ea2e0fea6', path: '', url: 'http://172.31.39.69:8080')], contextPath: 'testapp', war: '**/*.war'  
       }    
     }
     stage('contionuestesting')
     {
       steps
       {
        git 'https://github.com/Vijay01234/functional-testing.git'
        sh '''java -jar  /var/lib/jenkins/workspace/declarativepipeline/testing.jar'''
       }
     } 
     stage('contionuesdelivary')
     {
       steps
       {
         deploy adapters: [tomcat9(credentialsId: '443a7cf2-3c77-4440-8a31-cfdad56bde1d', path: '', url: 'http://172.31.38.227:8080')], contextPath: 'prodapp', war: '**/*.war'
       } 
     }
     
    }     
}

