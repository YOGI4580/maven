node('master') 
{
    stage('ContinuiousDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuiousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuiousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '1525e980-51d6-45cf-9736-2ceea79b55e5', path: '', url: 'http://172.31.7.36:8080')], contextPath: 'qaapp', war: '**/*.war'
    }
    stage('ContunuiousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/Scripted/testing.jar'
    }
    stage('ContnuiousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '1525e980-51d6-45cf-9736-2ceea79b55e5', path: '', url: 'http://172.31.7.182:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
