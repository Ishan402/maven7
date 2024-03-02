pipeline
{
  agent any
  stages
  {
    stage('Continuous Download')
    {
      steps
      {
        git 'https://github.com/Ishan402/maven7.git'
      }
    }
    stage('Continuous Build')
    {
      steps
      {
        sh 'mvn package'
      }
    }
    stage('Continuous Deployment')
    {
      steps
      {
        deploy adapters: [tomcat9(credentialsId: 'fc9f595b-cd17-4c21-802d-a37db5282bd0', path: '', url: 'http://172.31.84.253:8080')], contextPath: 'testapp', war: '**/*.war'
      }
    }
    stage('Continuous Testing')
    {
      steps
      {
        git 'https://github.com/intelliqittrainings/FunctionalTesting'
        sh 'java -jar /root/.jenkins/workspace/DeclarativePipeline1/testing.jar'
      }
    }
    stage('Continuous Delivery')
    {
      steps
      {
        deploy adapters: [tomcat9(credentialsId: 'fc9f595b-cd17-4c21-802d-a37db5282bd0', path: '', url: 'http://172.31.94.225:8080')], contextPath: 'prodapp', war: '**/*.war'
      }
    }
   }
}
