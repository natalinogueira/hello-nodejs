pipeline {

  agent any

 /* options{
    timestamps()
  }*/

  stages {

    stage("COMPILACAO & TESTE"){
      steps{
        echo '...TESTE...'
      }
    } 
    stage("ANALISE DE QUALIDADE"){
      steps{
        sh 'mvn clean package'
      }
 
    }
    stage("RESULTADO DE ANALISE"){
      steps{
        echo '...TESTE...'
      }

    }
    stage("SALVANDO ARTEFATO"){
      steps{
        echo '...TESTE...'
      }

    }
    stage("DEPLOY PRODUCAO"){
      steps{
        echo '...TESTE...'
      }

    }

  }

  post{
    always{
      echo "Finalizado pipeline"
    }
  }

}
