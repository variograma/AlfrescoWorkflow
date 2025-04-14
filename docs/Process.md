# Variograma.AlfrescoWorkflow.Model.Process
A process describes a running instance of a process definition.  When a new deployment includes a process definition that is already deployed with the same key, the newly deployed process definition will be considered a new version of the same process definition. By default processes will keep running in the process definition they are started in. But new processes can be started in the latest version of a process definition by using the processDefinitionKey parameter.  In non-network deployments, administrators can see all processes and perform all operations on tasks. In network deployments, network administrators can see processes in their network and perform all operations on tasks in their network. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** | The unique id of this process | 
**ProcessDefinitionId** | **string** | The unique identity of the owning process definition | [optional] 
**BusinessKey** | **string** | The business key | [optional] 
**StartedAt** | **DateTime** | The date time this process started | [optional] 
**EndedAt** | **DateTime** | The date time this process started | [optional] 
**DurationInMs** | **int** | The duration of this process | [optional] 
**StartActivityDefinitionId** | **string** | The id of the first activity in the process | [optional] 
**EndActivityDefinitionId** | **string** | The id of the last activity in the process | [optional] 
**StartUserId** | **string** | The id of the user who started the process | [optional] 
**DeleteReason** | **string** | The reason this process was canceled | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

