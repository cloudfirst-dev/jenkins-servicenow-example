node('nodejs') {
  stage 'build'
  openshiftBuild(buildConfig: 'servicenow-example', showBuildLogs: 'true')

  def response = serviceNow_createChange serviceNowConfiguration: [instance: 'dev59729', producerId: '563504cc47410200e90d87e8dee490e2'], credentialsId: 'servicenow'
  def jsonSlurper = new JsonSlurper()
  def createResponse = jsonSlurper.parseText(response.content)
  def sysId = createResponse.result.sys_id
  def changeNumber = createResponse.result.number

  stage 'deploy'
  openshiftDeploy(deploymentConfig: 'servicenow-example')
}