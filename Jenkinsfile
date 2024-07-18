pipeline{
  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')
  }

  stages{
    stage('Clone App Repo'){
      steps {
        dir('App') {
          git branch: 'main' , url: 'https://github.com/kvmallika/${component}'
        }
      }
    }
    stage('Helm Deploy') {
      steps {
        sh 'helm upgrade -i ${component} . -f APP/values.yaml'
      }
    }
  }
}