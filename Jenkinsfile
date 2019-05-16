node('nodejs') {
  stage 'build'
  openshiftBuild(buildConfig: 'servicenow-example', showBuildLogs: 'true')

  def response = serviceNow_createChange serviceNowConfiguration: [instance: 'dev59729', producerId: '563504cc47410200e90d87e8dee490e2'], credentialsId: 'servicenow'
  print(response.content)

  stage 'deploy'
  openshiftDeploy(deploymentConfig: 'servicenow-example')
}