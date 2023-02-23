pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
               git 'https://github.com/laxmikarna/maven89.git'
     
            }
            
        }
        stage('ContinuousBuild')
        {
            steps
            {
               sh 'mvn package'    
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '5af983ad-6cd7-4d5c-b485-30923bb6441f', path: '', url: 'http://172.31.90.109:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh '''java -jar /var/lib/jenkins/workspace/Declarativepipeline1/testing.jar


'''
            }
        }
        stage('ContDelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '5af983ad-6cd7-4d5c-b485-30923bb6441f', path: '', url: 'http://172.31.80.237:8080')], contextPath: 'prodapp', war: '**/*.war' 
            }
        }
    }
}
