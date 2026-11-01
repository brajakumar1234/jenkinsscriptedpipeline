node('built-in') {
   stage('continuousdownload') 
   {
       git 'https://github.com/IntelliqDevops/maven.git'
   }
   stage('continuousbuild') {
       sh 'mvn package'
   }
   stage('continuousDeployement') {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'f4fbfd69-a36e-466a-985b-3e635392c1c2', path: '', url: 'http://172.31.22.41:8080')], contextPath: 'pipeline', war: '**/*.war'
   }
   stage('continuoustesting') {
       git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
       sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
   }
    stage('continuous Delivery') {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'f4fbfd69-a36e-466a-985b-3e635392c1c2', path: '', url: 'http://172.31.25.122:8080')], contextPath: 'prod', war: '**/*.war'
   }
 
}
