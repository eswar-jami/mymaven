pipeline
{
    agent any
    stages
    {
        stage('ContiDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContiBulid')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContiDeploment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a69d7c6d-717a-4a3e-a9d8-3b553d79b960', path: '', url: 'http://172.31.23.10:8080')], contextPath: 'newtestapp', war: '**/*.war'
            }
        }
        stage('ContiTest')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContiDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a69d7c6d-717a-4a3e-a9d8-3b553d79b960', path: '', url: 'http://172.31.23.10:8080')], contextPath: 'newprodapp', war: '**/*.war'
            }
        }
    }
}
