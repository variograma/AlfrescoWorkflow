# Variograma.AlfrescoWorkflow.Model.Deployment
A deployment resource represents one file inside a deployment.  Process files, forms and perhaps some other files are authored in a separate environment. The act of deployment brings them into the runtime workflow engine.  A deployment is a collection of files that include all resources to specify one or more process definitions. After deployment, the included process definitions are known to the workflow runtime engine and new processes can be started.  Users can then continue to edit the process and other files in their authoring environment like e.g. our eclipse based process editor. A redeployment will result in a complete separate deployment containing new versions of the process definition.  When a process definition inside a new deployment has the same key as an existing process definition, then it is considered a new version of the existing process definition. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** |  | 
**Name** | **string** |  | [optional] 
**Category** | **string** |  | [optional] 
**DeployedAt** | **DateTime** |  | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

