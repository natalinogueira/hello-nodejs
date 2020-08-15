pipeline {
    agent any

   options{
       // timestamps()
        //timeout(time: 10 , unit:'SECONDS')
        skipDefaultCheckout()
    }

    environment {
        CURRENT_PATH=pwd()
        INFRA='CLOUD'
    }
   
    parameters {
        choice(name:'DEPLOY',choices:['DEV','HOMOLOG','PROD'], description:'Definir DEPLOY')
    }
   
    stages {
        
        /*stage('CleanUP'){
            steps{
              cleanWs()   
            }
        }*/
        
       /* stage('Criando Arquivos'){
            steps{
                sh "mkdir $WORKSPACE/arquivos"
                
                dir("$WORKSPACE/arquivos"){
                  sh 'touch teste'
                  sh 'ls -l'
                }
                
                sh 'ls -l ; pwd'
            }
        }*/
        
        stage('CHECKOUT'){
            steps{
                git credentialsId: '8f71f4be-0fc9-4d3e-93d6-e53c4149bc42', url: 'https://github.com/natalinogueira/hello-nodejs.git'
            }
        }
        
        stage('Variaveis') {
            when{
                anyOf {
                    environment name: 'INFRA', value: 'CLOUD'
                    environment name: 'DEPLOY', value: 'HOMOLOG'
                }       
            }
            steps {
                echo "Valor em CURRENT_PATH: $CURRENT_PATH"
                echo "Valor de INFRA: $INFRA"
            }
        }
        stage('INPUT'){
            steps{
               input 'Deseja continuar?'
               // input messsage: 'valor',submitter:'root'
            }
        }
        stage('Print DEPLOY') {
            steps{
                /*
                sh 'sleep 15'
                */
                echo "Conteúdo de deploy: ${params.DEPLOY}"
            }
        }
        
    }
    post{
    always{
        echo "Always no post actions"
    }
    success{
        mail to: 'root@localhost', subject:"Build ${BUILD_TAG} finalizada com sucesso", body:"Build_Success"
    }
    failure{
        mail to: 'root@localhost', subject:"Build ${BUILD_TAG} finalizada com erro", body:"Build_Error"
    }
}
}

