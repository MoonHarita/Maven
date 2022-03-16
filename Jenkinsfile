pipeline

{ 
 
  agent any
  
  stages
   
 {
       
    stage('ContiDownload')
   
    {
           
      steps
        
      {
        
        git 'https://github.com/MoonHarita/Maven.git'
           
      }
   
    }
        
    stage('ContBuild')
       
    {
            
      steps
            
      {
            
        sh 'mvn package'
            
      }
        
    }
        
    stage('ContDeploy')
        
    {
          
      steps
           
      {
             
       deploy adapters: [tomcat9(credentialsId: '98cf49fe-c3fb-4735-bca3-b96513c9f772', path: '', url: 'http://172.31.20.51:8080')], contextPath: 'test1', war: '**/*.war'
         
      }
       
    }
        
    stage('ContTesting')
     
    {
           
      steps
       
      {
              
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
         
       sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar'
             
 
     }
       
    }
        
    stage('ContDelivery')
       
    {
            
      steps
           
      {
               
        deploy adapters: [tomcat9(credentialsId: '98cf49fe-c3fb-4735-bca3-b96513c9f772', path: '', url: 'http://172.31.42.188:8080')], contextPath: 'prod1', war: '**/*.war'
              
         
      }
     
    }

        
 
  }


}

