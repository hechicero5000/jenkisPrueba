import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}

pipeline {
  agent { label 'principal' } // Asegúrate de que este agente sea tu máquina Windows
  environment {
    appName = "variable"
  }
  stages {
    stage("Paso 1 - Ejecutar en Windows") {
      steps {
        script {
          // Usa 'bat' para comandos de CMD o 'powershell' para comandos de PowerShell
          bat "echo 'hola mundo desde Windows'"
          // o
          // powershell "Write-Host 'hola mundo desde Windows con PowerShell'"
        }
      }
    }
  }
  post {
    always {
      // deleteDir() es un comando de Groovy/Jenkins, no un comando de shell.
      // Puede que necesites ajustar cómo se borra el directorio de trabajo si tienes problemas.
      // deleteDir() // Esta línea debería funcionar bien si Jenkins tiene permisos.

      // Usa 'bat' para comandos de shell en Windows
      bat "echo 'Fase always en Windows'"
    }
    success {
      bat "echo 'Fase success en Windows'"
    }
    failure {
      bat "echo 'Fase failure en Windows'"
    }
  }
}
