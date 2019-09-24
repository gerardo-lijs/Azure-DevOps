# How to build .NET Core 3.0 in Azure Devops Pipeline (2019-09-24)
Sample pipeline to work with netcore3 in Azure Devops. This will change soon once Microsoft directly supports netcore3 in Azure Devops and App Services

## Content
* [YAML Pipeline](azure-pipelines.yml)  
* [Global JSON](global.json)  

## Steps
* YAML Pipeline
We need to manually install netcore 3.0 using UseDotNet@2 task.

```
- task: UseDotNet@2
  displayName: 'Use dotnet sdk 3.0.100'
  inputs:
    packageType: sdk
    version: 3.0.100
```

* Global JSON
We need also need to add a global.json file to our project.

```json
{
  "sdk": {
    "version": "3.0.100"
  }
}
```

## Notes
* The pipeline build with --runtime win-x86 --self-contained which is needed to publish to App Services right now. But if you build other types of project you don't need this.
* This was writen in 24 September 2019, the day after official Net Core 3.0 release. Once Microsoft updates DevOps and Azure to support netcore3 directly this will change and you won't need this tweaks.'