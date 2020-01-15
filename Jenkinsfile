pipeline{
  agent { 
    node {
      label 'nodejs8' 
    } 
  }
  stages{
    stage ('Checkout codigo fuente'){
      steps{
        checkout scm
      }
    }
    stage ('Instalar dependencias'){
      steps{
        sh '''          
          npm install          
        '''
      }
    }
    stage ('Revisión calidad con LINT'){
      steps{
        sh '$(npm bin)/ng lint'
      }
    }
    stage ('Test Angular Cobertura') {
      steps{
        sh '''
            cd src
            $(npm bin)/run test -- --watch=false --code-coverage
            '''
      }
    }    
    stage ('Construcción Aplicación') {
      steps{
        sh '$(npm bin)/ng build --prod --build-optimizer'
      }
    }    
  }
}
