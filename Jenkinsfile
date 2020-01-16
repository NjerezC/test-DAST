pipeline{
  agent any
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
    stage ('test'){
      steps{
        sh '''
          npm run test -- --watch=false --code-coverage
        '''
      }      
    }
    stage ('Revisión calidad con LINT'){
      steps{
        sh '$(npm bin)/ng lint'
      }
    }       
    stage ('Construcción Aplicación') {
      steps{
        sh '$(npm bin)/ng build --prod --build-optimizer'
      }
    }
  }
}
