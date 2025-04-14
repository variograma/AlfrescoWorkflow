# Variograma.AlfrescoWorkflow.Model.Task
A task describes one task for a human user. 

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**Id** | **string** | The unique id of this task | 
**ProcessId** | **string** | The containing process&#39;s unique id | [optional] 
**ProcessDefinitionId** | **string** | The unique identity of the owning process definition | [optional] 
**ActivityDefinitionId** | **string** | The activity id of this task | [optional] 
**Name** | **string** | The text name of this task | [optional] 
**Description** | **string** | The description of this task | [optional] 
**DueAt** | **DateTime** | The date time this task is due | [optional] 
**StartedAt** | **DateTime** | The date time this task started | [optional] 
**EndedAt** | **DateTime** | The date time this task started | [optional] 
**DurationInMs** | **int** | The duration of this task | [optional] 
**Priority** | **int** | The numeric priority of this task | [optional] 
**Owner** | **string** | The id of the user who owns this task | [optional] 
**Assignee** | **string** | The id of the user who is currently assigned this task | [optional] 
**FormResourceKey** | **string** | The key of the form for this task | [optional] 
**State** | **string** | The state of this task | [optional] 
**Variables** | [**List&lt;Variable&gt;**](Variable.md) | An array of variables for this task | [optional] 

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

