# Variograma.AlfrescoWorkflow.Api.TasksApi

All URIs are relative to *http://localhost/alfresco/api/-default-/public/workflow/versions/1*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateTaskItem**](TasksApi.md#createtaskitem) | **POST** /tasks/{taskId}/items | Create an item |
| [**CreateTaskVariables**](TasksApi.md#createtaskvariables) | **POST** /tasks/{taskId}/variables | Create or update variables |
| [**DeleteTaskItem**](TasksApi.md#deletetaskitem) | **DELETE** /tasks/{taskId}/items/{itemId} | Delete an item |
| [**DeleteTaskVariable**](TasksApi.md#deletetaskvariable) | **DELETE** /tasks/{taskId}/variables/{variableName} | Delete a variable |
| [**GetTask**](TasksApi.md#gettask) | **GET** /tasks/{taskId} | Get a task |
| [**GetTaskFormModel**](TasksApi.md#gettaskformmodel) | **GET** /tasks/{taskId}/task-form-model | Get a task form model |
| [**ListTaskCandidates**](TasksApi.md#listtaskcandidates) | **GET** /tasks/{taskId}/candidates | List task candidates |
| [**ListTaskItems**](TasksApi.md#listtaskitems) | **GET** /tasks/{taskId}/items | List items |
| [**ListTaskVariables**](TasksApi.md#listtaskvariables) | **GET** /tasks/{taskId}/variables | List variables |
| [**ListTasks**](TasksApi.md#listtasks) | **GET** /tasks | List tasks |
| [**ListTasksForProcess**](TasksApi.md#listtasksforprocess) | **GET** /processes/{processId}/tasks | List tasks for a process |
| [**UpdateTask**](TasksApi.md#updatetask) | **PUT** /tasks/{taskId} | Update a task |
| [**UpdateTaskVariable**](TasksApi.md#updatetaskvariable) | **PUT** /tasks/{taskId}/variables/{variableName} | Create or update a variable |

<a id="createtaskitem"></a>
# **CreateTaskItem**
> ItemPaging CreateTaskItem (string taskId, ItemBody itemBody)

Create an item

Creates an item for a given task **taskId**.  If the item  already is part of that task the request will have no effect.  **Note:** You can create more than one item by specifying a list of items in the JSON body like this:  ```JSON [   {      \"id\": \"1ff9da1a-ee2f-4b9c-8c34-44665e844444\"   },   {      \"id\": \"1ff9da1a-ee2f-4b9c-8c34-44665e855555\"   } ] ``` If you specify a list as input, then a paginated list rather than an entry is returned in the response body. For example:  ```JSON {   \"list\": {     \"pagination\": {       \"count\": 2,       \"hasMoreItems\": false,       \"totalItems\": 2,       \"skipCount\": 0,       \"maxItems\": 100     },     \"entries\": [       {         \"entry\": {           ...         }       },       {         \"entry\": {           ...         }       }     ]   } } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateTaskItemExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var itemBody = new ItemBody(); // ItemBody | The nodeId of the item

            try
            {
                // Create an item
                ItemPaging result = apiInstance.CreateTaskItem(taskId, itemBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.CreateTaskItem: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateTaskItemWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create an item
    ApiResponse<ItemPaging> response = apiInstance.CreateTaskItemWithHttpInfo(taskId, itemBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.CreateTaskItemWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **itemBody** | [**ItemBody**](ItemBody.md) | The nodeId of the item |  |

### Return type

[**ItemPaging**](ItemPaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Successful response |  -  |
| **400** | Invalid parameter: **itemBody** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createtaskvariables"></a>
# **CreateTaskVariables**
> VariableEntry CreateTaskVariables (string taskId, Variable variable)

Create or update variables

Create or update a variable for the task **taskId**. If the variable does not exist yet, it will be created.         **Note:** You can create or update more than one variable by  specifying a list of variables in the JSON body like this:  ```JSON [   {     \"name\": \"string\",     \"value\": \"string\",     \"type\": \"string\"   },   {     \"name\": \"string\",     \"value\": \"string\",     \"type\": \"string\"   } ] ``` If you specify a list as input, then a paginated list rather than an entry is returned in the response body. For example:  ```JSON {   \"list\": {     \"pagination\": {       \"count\": 2,       \"hasMoreItems\": false,       \"totalItems\": 2,       \"skipCount\": 0,       \"maxItems\": 100     },     \"entries\": [       {         \"entry\": {           ...         }       },       {         \"entry\": {          ...         }       }     ]   } } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateTaskVariablesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var variable = new Variable(); // Variable | A variable

            try
            {
                // Create or update variables
                VariableEntry result = apiInstance.CreateTaskVariables(taskId, variable);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.CreateTaskVariables: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateTaskVariablesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create or update variables
    ApiResponse<VariableEntry> response = apiInstance.CreateTaskVariablesWithHttpInfo(taskId, variable);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.CreateTaskVariablesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **variable** | [**Variable**](Variable.md) | A variable |  |

### Return type

[**VariableEntry**](VariableEntry.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Successful response |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletetaskitem"></a>
# **DeleteTaskItem**
> void DeleteTaskItem (string taskId, string itemId)

Delete an item

Deletes the item with the specified **itemId** from the task with the specified **taskId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteTaskItemExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var itemId = "itemId_example";  // string | The identifier of an item.

            try
            {
                // Delete an item
                apiInstance.DeleteTaskItem(taskId, itemId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.DeleteTaskItem: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteTaskItemWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete an item
    apiInstance.DeleteTaskItemWithHttpInfo(taskId, itemId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.DeleteTaskItemWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **itemId** | **string** | The identifier of an item. |  |

### Return type

void (empty response body)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Successful response |  -  |
| **401** | Authentication failed |  -  |
| **404** | The **taskId** does not exist or the **itemId** does not exist |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deletetaskvariable"></a>
# **DeleteTaskVariable**
> void DeleteTaskVariable (string taskId, string variableName)

Delete a variable

Deletes the variable with the specified **variableName** from the task with the specified **taskId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteTaskVariableExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var variableName = "variableName_example";  // string | The name of a variable.

            try
            {
                // Delete a variable
                apiInstance.DeleteTaskVariable(taskId, variableName);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.DeleteTaskVariable: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteTaskVariableWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a variable
    apiInstance.DeleteTaskVariableWithHttpInfo(taskId, variableName);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.DeleteTaskVariableWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **variableName** | **string** | The name of a variable. |  |

### Return type

void (empty response body)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **204** | Successful response |  -  |
| **401** | Authentication failed |  -  |
| **404** | The **taskId** does not exist or the **variableName** does not exist |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gettask"></a>
# **GetTask**
> TaskEntry GetTask (string taskId, List<string> properties = null)

Get a task

Gets the task identified by **taskId**.  An authenticated user will have access to a task if the user has started the process or if the user is involved in any of the process’s tasks. In a network, only tasks that are inside the given network are returned.  In non-network deployments, administrators can see all processes and perform all operations on tasks. In network deployments, network administrators can see all processes in their network and perform all operations on tasks in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetTaskExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a task
                TaskEntry result = apiInstance.GetTask(taskId, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.GetTask: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTaskWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a task
    ApiResponse<TaskEntry> response = apiInstance.GetTaskWithHttpInfo(taskId, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.GetTaskWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**TaskEntry**](TaskEntry.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="gettaskformmodel"></a>
# **GetTaskFormModel**
> TaskFormModelPaging GetTaskFormModel (string taskId, int? skipCount = null, int? maxItems = null, List<string> properties = null)

Get a task form model

Gets the model of the task form type definition.  An authenticated user will have access to  access to all task form models. In a network, only task form models that are inside the given network are returned. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetTaskFormModelExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a task form model
                TaskFormModelPaging result = apiInstance.GetTaskFormModel(taskId, skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.GetTaskFormModel: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetTaskFormModelWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a task form model
    ApiResponse<TaskFormModelPaging> response = apiInstance.GetTaskFormModelWithHttpInfo(taskId, skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.GetTaskFormModelWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**TaskFormModelPaging**](TaskFormModelPaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems** or **skipCount** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtaskcandidates"></a>
# **ListTaskCandidates**
> CandidatePaging ListTaskCandidates (string taskId, int? skipCount = null, int? maxItems = null, List<string> properties = null)

List task candidates

Gets a list of candidate users and groups for the specified task **taskId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListTaskCandidatesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // List task candidates
                CandidatePaging result = apiInstance.ListTaskCandidates(taskId, skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.ListTaskCandidates: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTaskCandidatesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List task candidates
    ApiResponse<CandidatePaging> response = apiInstance.ListTaskCandidatesWithHttpInfo(taskId, skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.ListTaskCandidatesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**CandidatePaging**](CandidatePaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems** or **skipCount** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtaskitems"></a>
# **ListTaskItems**
> ItemPaging ListTaskItems (string taskId, int? skipCount = null, int? maxItems = null, List<string> properties = null)

List items

Gets a list of items for the specified task **taskId**.  An authenticated user will have access to a task's items if the user has started the process or if the user is involved in any of the process’s tasks.  In a network, only items for a process that is inside the given network are returned.  In non-network deployments, administrators can see all items and perform all operations  on those items. In network deployments, network administrators can see all items in their network and perform all operations on items in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListTaskItemsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // List items
                ItemPaging result = apiInstance.ListTaskItems(taskId, skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.ListTaskItems: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTaskItemsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List items
    ApiResponse<ItemPaging> response = apiInstance.ListTaskItemsWithHttpInfo(taskId, skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.ListTaskItemsWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**ItemPaging**](ItemPaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems** or **skipCount** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtaskvariables"></a>
# **ListTaskVariables**
> VariablePaging ListTaskVariables (string taskId, int? skipCount = null, int? maxItems = null, List<string> properties = null, string where = null)

List variables

Gets a list of variables for the specified task **taskId**.  An authenticated user will have access to a tasks variables if the user has started the process or if the user is involved in any of the process’s tasks.  In a network, only variables for a process that is inside the given network are returned.  In non-network deployments, administrators can see all variables and perform all operations  on those variable. In network deployments, network administrators can see all variables in  their network and perform all operations on variables in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListTaskVariablesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 
            var where = "where_example";  // string | A string to restrict the returned objects by using a predicate. (optional) 

            try
            {
                // List variables
                VariablePaging result = apiInstance.ListTaskVariables(taskId, skipCount, maxItems, properties, where);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.ListTaskVariables: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTaskVariablesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List variables
    ApiResponse<VariablePaging> response = apiInstance.ListTaskVariablesWithHttpInfo(taskId, skipCount, maxItems, properties, where);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.ListTaskVariablesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |
| **where** | **string** | A string to restrict the returned objects by using a predicate. | [optional]  |

### Return type

[**VariablePaging**](VariablePaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems**, **skipCount**, or **where** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtasks"></a>
# **ListTasks**
> TaskPaging ListTasks (int? skipCount = null, int? maxItems = null, List<string> properties = null, List<string> orderBy = null, string where = null)

List tasks

Gets a list of tasks visible to the authenticated user.  Tasks are returned for which the authenticated user is the assignee  or a candidate. If networks are enabled, the only tasks that are inside the given network are returned.  In non-network deployments, administrators can see all processes and perform all operations on tasks. In network deployments, network administrators can see all processes in their network and perform all operations on tasks in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListTasksExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 
            var orderBy = new List<string>(); // List<string> | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  (optional) 
            var where = "where_example";  // string | A string to restrict the returned objects by using a predicate. (optional) 

            try
            {
                // List tasks
                TaskPaging result = apiInstance.ListTasks(skipCount, maxItems, properties, orderBy, where);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.ListTasks: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTasksWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List tasks
    ApiResponse<TaskPaging> response = apiInstance.ListTasksWithHttpInfo(skipCount, maxItems, properties, orderBy, where);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.ListTasksWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |
| **orderBy** | [**List&lt;string&gt;**](string.md) | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  | [optional]  |
| **where** | **string** | A string to restrict the returned objects by using a predicate. | [optional]  |

### Return type

[**TaskPaging**](TaskPaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems**, **skipCount**, **orderBy**, or **where** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listtasksforprocess"></a>
# **ListTasksForProcess**
> TaskPaging ListTasksForProcess (string processId, int? skipCount = null, int? maxItems = null, List<string> properties = null, List<string> orderBy = null)

List tasks for a process

Gets a list of tasks for the specified process **processId**.  An authenticated user will have access to a processes tasks if the user has started the process or if the user is involved in any of the process’s tasks.  In a network, only tasks for a process that is inside the given network are returned.  In non-network deployments, administrators can see all tasks and perform all operations  on those tasks. In network deployments, network administrators can see all tasks in their network and perform all operations on tasks in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListTasksForProcessExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 
            var orderBy = new List<string>(); // List<string> | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  (optional) 

            try
            {
                // List tasks for a process
                TaskPaging result = apiInstance.ListTasksForProcess(processId, skipCount, maxItems, properties, orderBy);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.ListTasksForProcess: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListTasksForProcessWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List tasks for a process
    ApiResponse<TaskPaging> response = apiInstance.ListTasksForProcessWithHttpInfo(processId, skipCount, maxItems, properties, orderBy);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.ListTasksForProcessWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
| **skipCount** | **int?** | The number of entities that  exist in the collection before those included in this list. | [optional]  |
| **maxItems** | **int?** | The maximum number of items to return in the list. | [optional]  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |
| **orderBy** | [**List&lt;string&gt;**](string.md) | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  | [optional]  |

### Return type

[**TaskPaging**](TaskPaging.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: value of **maxItems**, **skipCount**, or **orderBy** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatetask"></a>
# **UpdateTask**
> TaskEntry UpdateTask (string taskId, TaskBody taskBody, int? select = null)

Update a task

Updates the state of the task **taskId**.  To perform a task action the authenticated user must be the assignee  or a candidate. If networks is enabled, the task action is only performed  if the task is inside the given network.  In non-network deployments, administrators can perform all operations on  tasks. In network deployments, network administrators can see all tasks  in their network and perform all operations on tasks in their network.  You use the **select** parameter in the URL to specify a comma-separated list of properties in the task that you want to update. Use the JSON body to specify the new values for those properties.  So for example to change the state of task **123** to **completed**, use this URL http://localhost:8080/alfresco/api/-default-/public/workflow/versions/1/tasks/123?select=state, and provide this request body:  ```JSON {   \"state\": \"completed\" } ``` State Transitions =================  Clients can invoke actions by assigning an allowed value to the state property of a task. The select parameter can be used to allow for a partial update of the resource. Alfresco will check for illegal state transitions and return an HTTP Bad Request (Response 400) if an illegal state transition is attempted. There are five state transitions, completing, claiming, unclaiming, delegating, resolving.  Completing a task - -- -- -- -- -- -- -- --  If variables are included in the JSON body, they will be set in the task and then the process will continue.  To complete a task, the authenticated user must be the assignee of the task, the owner of the task, or have started the process.  In non-network deployments, administrators can perform this task operation on all tasks. In network deployments, network administrators can perform this action on all tasks in their network.  Here's an example PUT request  ``` /tasks/123?select=state,variables ``` Here's is a corresponding PUT request body:  ```JSON {   “state : “completed”,   “variables” : [   {     \"name\" : \"bpm_priority\",     \"type\" : \"d_int\",     \"value\" : 1,     \"scope\" : \"global\"   }  ] } ```  Claiming a task - -- -- -- -- -- -- -- --  To claim a task, the authenticated user must be the assignee of the task, the owner of the task, or have started the process.  Here's an example PUT request  ``` /tasks/123?select=state ``` Here's a corresponding PUT request body:  ```JSON {   “state : “claimed” } ```  Unclaiming a task - -- -- -- -- -- -- -- --  This removes the current assignee of the task.  To unclaim a task, the authenticated user must be the assignee of the task, the owner of the task, or have started the process.  Here's an example PUT request  ``` /tasks/123?select=state ``` Here's a corresponding PUT request body:  ```JSON {   “state : “unclaimed” } ```  Delegating a task - -- -- -- -- -- -- -- --  This delegates the task from the owner to an assignee. The result is the same as if the assignee had claimed the task, but the task can then be resolved and the owner will become the assignee again.  To delegate a task, the authenticated user must be the assignee of the task and the assignee must be different from the owner.  Here's an example PUT request  ``` /tasks/123?select=state,assignee ``` Here's a corresponding PUT request body:  ```JSON {   “state : “delegated”,   “assignee : “Kermit” } ``` Resolving a task - -- -- -- -- -- -- -- --  This returns a delegated task back to the owner. In order to delegate a task, the authenticated user must be the assignee of the task and the assignee must be different from the owner.  To resolve a task, the authenticated user must be the assignee of the task, the owner of the task, or have started the process.  Here's an example PUT request  ``` /tasks/123?select=state ``` Here's a corresponding PUT request body:  ```JSON {   “state : “resolved” } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class UpdateTaskExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var taskBody = new TaskBody(); // TaskBody | An object containing the properties to be updated
            var select = 56;  // int? | A string specifying a required subset of properties to be returned for an entity or list of entities. Properties are separated by commas. (optional) 

            try
            {
                // Update a task
                TaskEntry result = apiInstance.UpdateTask(taskId, taskBody, select);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.UpdateTask: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateTaskWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Update a task
    ApiResponse<TaskEntry> response = apiInstance.UpdateTaskWithHttpInfo(taskId, taskBody, select);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.UpdateTaskWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **taskBody** | [**TaskBody**](TaskBody.md) | An object containing the properties to be updated |  |
| **select** | **int?** | A string specifying a required subset of properties to be returned for an entity or list of entities. Properties are separated by commas. | [optional]  |

### Return type

[**TaskEntry**](TaskEntry.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: **taskBody** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="updatetaskvariable"></a>
# **UpdateTaskVariable**
> VariableEntry UpdateTaskVariable (string taskId, string variableName, Variable variableBody)

Create or update a variable

Creates or updates a specific variable **variableName** for a given task **taskId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class UpdateTaskVariableExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new TasksApi(config);
            var taskId = "taskId_example";  // string | The identifier of a task.
            var variableName = "variableName_example";  // string | The name of a variable.
            var variableBody = new Variable(); // Variable | A variable

            try
            {
                // Create or update a variable
                VariableEntry result = apiInstance.UpdateTaskVariable(taskId, variableName, variableBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling TasksApi.UpdateTaskVariable: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the UpdateTaskVariableWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create or update a variable
    ApiResponse<VariableEntry> response = apiInstance.UpdateTaskVariableWithHttpInfo(taskId, variableName, variableBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling TasksApi.UpdateTaskVariableWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **taskId** | **string** | The identifier of a task. |  |
| **variableName** | **string** | The name of a variable. |  |
| **variableBody** | [**Variable**](Variable.md) | A variable |  |

### Return type

[**VariableEntry**](VariableEntry.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: **variableBody** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **taskId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

