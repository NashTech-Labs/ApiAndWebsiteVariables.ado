# ApiAndWebsiteVariables.ado


## Pipeline Requirements

The pipeline requires the following parameters to be defined:
Paramaters:


| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| enableApiAndWebsiteVariables | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| enableWebsiteVariables | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| enableStyleAPIVariables  | boolean | 'false' | 'true'/'false' | Required | This is a Boolean value to define whether to use this template or not  |
| websiteAppServiceNames | string | | | Optional | |
| websiteArchivePattern | string | | | Optional | |
| websiteExtractFolder | string | | | Optional | |
| websitePackageId | string | | | Optional | |
| websitePacakgeVersion | string | | | Optional | |
| websiteImage | string | | | Optional | |
| websiteAKSApps | string | | | Optional | |
| websiteAKSAppsForBlueGreen | string | | | Optional | |
| websiteWorkloadName | string | | | Optional | |
| product.name | string | | | Required | |

  These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases



### Direct use of templates

You can directly call a particular template as per the requirement. for example: 

```yaml

 # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name:  your_username/Repo_name
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  - template: frameWork/common/setVariables/SetApiAndWebsiteVariables.yml@Template
      parameters:
         ${{ insert }}: ${{ parameters }}
         apiAppServiceNames: ${{ parameters.apiAppServiceNames }}
         apiArchivePattern: ${{ parameters.apiArchivePattern }}
         apiExtractFolder: ${{ parameters.apiExtractFolder }}
         apiPackageId: ${{ parameters.apiPackageId }}
         apiPacakgeVersion: ${{ parameters.apiPacakgeVersion }}
         websiteAKSApps: ${{ parameters.websiteAKSApps }}
         websiteAKSAppsForBlueGreen: ${{ parameters.websiteAKSAppsForBlueGreen }}
         websiteWorkloadName: ${{ parameters.websiteWorkloadName }}
         websiteAppServiceNames: ${{ parameters.websiteAppServiceNames }}
         websiteArchivePattern: ${{ parameters.websiteArchivePattern }}
         websiteExtractFolder: ${{ parameters.websiteExtractFolder }}
         websiteImage: claimsstudio: ${{ parameters.websiteImage }}
         websitePackageId: ${{ parameters.websitePackageId }}
         websitePacakgeVersion: ${{ parameters.websitePacakgeVersion }}



  ```

Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

