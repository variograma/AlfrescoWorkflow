# Variograma.AlfrescoWorkflow.Api.ProcessesApi

All URIs are relative to *http://localhost/alfresco/api/-default-/public/workflow/versions/1*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**CreateProcess**](ProcessesApi.md#createprocess) | **POST** /processes | Create a process |
| [**CreateProcessItem**](ProcessesApi.md#createprocessitem) | **POST** /processes/{processId}/items | Create an item |
| [**CreateProcessVariable**](ProcessesApi.md#createprocessvariable) | **PUT** /processes/{processId}/variables/{variableName} | Create or update a variable |
| [**CreateProcessVariables**](ProcessesApi.md#createprocessvariables) | **POST** /processes/{processId}/variables | Create or update variables |
| [**DeleteProcess**](ProcessesApi.md#deleteprocess) | **DELETE** /processes/{processId} | Delete a process |
| [**DeleteProcessItem**](ProcessesApi.md#deleteprocessitem) | **DELETE** /processes/{processId}/items/{itemId} | Delete an item |
| [**DeleteProcessVariable**](ProcessesApi.md#deleteprocessvariable) | **DELETE** /processes/{processId}/variables/{variableName} | Delete a variable |
| [**GetProcess**](ProcessesApi.md#getprocess) | **GET** /processes/{processId} | Get a process |
| [**ListProcessItems**](ProcessesApi.md#listprocessitems) | **GET** /processes/{processId}/items | List items |
| [**ListProcessVariables**](ProcessesApi.md#listprocessvariables) | **GET** /processes/{processId}/variables | List variables |
| [**ListProcesses**](ProcessesApi.md#listprocesses) | **GET** /processes | List processes |

<a id="createprocess"></a>
# **CreateProcess**
> ProcessEntry CreateProcess (ProcessBody processBody)

Create a process

Creates a new process.  In non-network deployments, any authenticated user can start a new process for any process definition.  If networks are enabled, the authenticated user can start a new process for a process definition in the user's network.  **Note:** You can start more than one process by specifying a list of process entries in the JSON body like this:  ```JSON [   {      \"processDefinitionKey\": \"activitiAdhoc\",      \"variables\": {         \"bpm_assignee\": \"fred\"     }   },   {      \"processDefinitionKey\": \"activitiAdhoc\",      \"variables\": {         \"bpm_assignee\": \"joe\"     } ] ``` If you specify a list as input, then a paginated list rather than an entry is returned in the response body. For example:  ```JSON {   \"list\": {     \"pagination\": {       \"count\": 2,       \"hasMoreItems\": false,       \"totalItems\": 2,       \"skipCount\": 0,       \"maxItems\": 100     },     \"entries\": [       {         \"entry\": {           ...         }       },       {         \"entry\": {           ...         }       }     ]   } } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateProcessExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processBody = new ProcessBody(); // ProcessBody | process properties

            try
            {
                // Create a process
                ProcessEntry result = apiInstance.CreateProcess(processBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.CreateProcess: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateProcessWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create a process
    ApiResponse<ProcessEntry> response = apiInstance.CreateProcessWithHttpInfo(processBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.CreateProcessWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processBody** | [**ProcessBody**](ProcessBody.md) | process properties |  |

### Return type

[**ProcessEntry**](ProcessEntry.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **400** | Invalid parameter: **processBody** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createprocessitem"></a>
# **CreateProcessItem**
> ItemPaging CreateProcessItem (string processId, ItemBody itemBody)

Create an item

Creates an item for process **processId**\".  If the item  already is part of that process the request will have no effect.  **Note:** You can create more than one item by specifying a list of items in the JSON body like this:  ```JSON [   {      \"id\": \"1ff9da1a-ee2f-4b9c-8c34-44665e844444\"   },   {      \"id\": \"1ff9da1a-ee2f-4b9c-8c34-44665e855555\"   } ] ``` If you specify a list as input, then a paginated list rather than an entry is returned in the response body. For example:  ```JSON {   \"list\": {     \"pagination\": {       \"count\": 2,       \"hasMoreItems\": false,       \"totalItems\": 2,       \"skipCount\": 0,       \"maxItems\": 100     },     \"entries\": [       {         \"entry\": {           ...         }       },       {         \"entry\": {           ...         }       }     ]   } } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateProcessItemExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var itemBody = new ItemBody(); // ItemBody | The **nodeId** of the item

            try
            {
                // Create an item
                ItemPaging result = apiInstance.CreateProcessItem(processId, itemBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.CreateProcessItem: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateProcessItemWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create an item
    ApiResponse<ItemPaging> response = apiInstance.CreateProcessItemWithHttpInfo(processId, itemBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.CreateProcessItemWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
| **itemBody** | [**ItemBody**](ItemBody.md) | The **nodeId** of the item |  |

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
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createprocessvariable"></a>
# **CreateProcessVariable**
> VariableEntry CreateProcessVariable (string processId, string variableName, VariableBody variableBody)

Create or update a variable

Creates or updates a specific variable **variableName** for process **processId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateProcessVariableExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var variableName = "variableName_example";  // string | The name of a variable.
            var variableBody = new VariableBody(); // VariableBody | A variable

            try
            {
                // Create or update a variable
                VariableEntry result = apiInstance.CreateProcessVariable(processId, variableName, variableBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.CreateProcessVariable: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateProcessVariableWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create or update a variable
    ApiResponse<VariableEntry> response = apiInstance.CreateProcessVariableWithHttpInfo(processId, variableName, variableBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.CreateProcessVariableWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
| **variableName** | **string** | The name of a variable. |  |
| **variableBody** | [**VariableBody**](VariableBody.md) | A variable |  |

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
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="createprocessvariables"></a>
# **CreateProcessVariables**
> VariableEntry CreateProcessVariables (string processId, VariableBody variableBody)

Create or update variables

Create or update a variable for a given process. If the variable does not exist yet, it will be created.           **Note:** You can create or update more than one variable by  specifying a list of variables in the JSON body like this:  ```JSON [   {     \"name\": \"string\",     \"value\": \"string\",     \"type\": \"string\"   },   {     \"name\": \"string\",     \"value\": \"string\",     \"type\": \"string\"   } ] ``` If you specify a list as input, then a paginated list rather than an entry is returned in the response body. For example:  ```JSON {   \"list\": {     \"pagination\": {       \"count\": 2,       \"hasMoreItems\": false,       \"totalItems\": 2,       \"skipCount\": 0,       \"maxItems\": 100     },     \"entries\": [       {         \"entry\": {           ...         }       },       {         \"entry\": {          ...         }       }     ]   } } ``` 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class CreateProcessVariablesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var variableBody = new VariableBody(); // VariableBody | A variable

            try
            {
                // Create or update variables
                VariableEntry result = apiInstance.CreateProcessVariables(processId, variableBody);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.CreateProcessVariables: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the CreateProcessVariablesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Create or update variables
    ApiResponse<VariableEntry> response = apiInstance.CreateProcessVariablesWithHttpInfo(processId, variableBody);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.CreateProcessVariablesWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
| **variableBody** | [**VariableBody**](VariableBody.md) | A variable |  |

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
| **400** | Invalid parameter: **variableBody** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteprocess"></a>
# **DeleteProcess**
> void DeleteProcess (string processId)

Delete a process

Deletes the process with the specified **processId**.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteProcessExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.

            try
            {
                // Delete a process
                apiInstance.DeleteProcess(processId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.DeleteProcess: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteProcessWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a process
    apiInstance.DeleteProcessWithHttpInfo(processId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.DeleteProcessWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |

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
| **404** | The processId does not exist |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteprocessitem"></a>
# **DeleteProcessItem**
> void DeleteProcessItem (string processId, string itemId)

Delete an item

Deletes the item with the specified **itemId** from the process with the specified **processId**. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteProcessItemExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var itemId = "itemId_example";  // string | The identifier of an item.

            try
            {
                // Delete an item
                apiInstance.DeleteProcessItem(processId, itemId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.DeleteProcessItem: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteProcessItemWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete an item
    apiInstance.DeleteProcessItemWithHttpInfo(processId, itemId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.DeleteProcessItemWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
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
| **404** | The **processId** does not exist or the **itemId** does not exist |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="deleteprocessvariable"></a>
# **DeleteProcessVariable**
> void DeleteProcessVariable (string processId, string variableName)

Delete a variable

Deletes the variable **variableName** from the process with the specified **processId**.

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteProcessVariableExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var variableName = "variableName_example";  // string | The name of a variable.

            try
            {
                // Delete a variable
                apiInstance.DeleteProcessVariable(processId, variableName);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.DeleteProcessVariable: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteProcessVariableWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a variable
    apiInstance.DeleteProcessVariableWithHttpInfo(processId, variableName);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.DeleteProcessVariableWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
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
| **404** | The **processId** does not exist or the **variableName** does not exist |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprocess"></a>
# **GetProcess**
> ProcessEntry GetProcess (string processId, List<string> properties = null)

Get a process

Gets the process identified by **processId**.  An authenticated user will have access to a process if the user has started the process or if the user is involved in any of the process’s tasks. In a network, only processes that are inside the given network are returned.  In non-network deployments, administrators can see all processes and perform all operations on tasks. In network deployments, network administrators can see all processes in their network and perform all operations on tasks in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetProcessExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a process
                ProcessEntry result = apiInstance.GetProcess(processId, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.GetProcess: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProcessWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a process
    ApiResponse<ProcessEntry> response = apiInstance.GetProcessWithHttpInfo(processId, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.GetProcessWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processId** | **string** | The identifier of a process. |  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**ProcessEntry**](ProcessEntry.md)

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
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprocessitems"></a>
# **ListProcessItems**
> ItemPaging ListProcessItems (string processId, int? skipCount = null, int? maxItems = null, List<string> properties = null)

List items

Gets a list of items for the specified process **processId**.  An authenticated user will have access to a processes items if the user has started the process or if the user is involved in any of the process’s tasks.  In a network, only items for a process that is inside the given network are returned.  In non-network deployments, administrators can see all items and perform all operations  on those items. In network deployments, network administrators can see all items in their network and perform all operations on items in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListProcessItemsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // List items
                ItemPaging result = apiInstance.ListProcessItems(processId, skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.ListProcessItems: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListProcessItemsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List items
    ApiResponse<ItemPaging> response = apiInstance.ListProcessItemsWithHttpInfo(processId, skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.ListProcessItemsWithHttpInfo: " + e.Message);
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
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprocessvariables"></a>
# **ListProcessVariables**
> VariablePaging ListProcessVariables (string processId, int? skipCount = null, int? maxItems = null, List<string> properties = null)

List variables

Gets a list of variables for the process **processId**.  An authenticated user will have access to a processes variables if the user has started  the process or if the user is involved in any of the process’s tasks.  In a network, only variables for a process that is inside the given network are returned.  In non-network deployments, administrators can see all variables and perform all operations  on those variable. In network deployments, network administrators can see all variables in  their network and perform all operations on variables in their network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListProcessVariablesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var processId = "processId_example";  // string | The identifier of a process.
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // List variables
                VariablePaging result = apiInstance.ListProcessVariables(processId, skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.ListProcessVariables: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListProcessVariablesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List variables
    ApiResponse<VariablePaging> response = apiInstance.ListProcessVariablesWithHttpInfo(processId, skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.ListProcessVariablesWithHttpInfo: " + e.Message);
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
| **400** | Invalid parameter: value of **maxItems** or **skipCount** is invalid  |  -  |
| **401** | Authentication failed |  -  |
| **404** | **processId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprocesses"></a>
# **ListProcesses**
> ProcessPaging ListProcesses (int? skipCount = null, int? maxItems = null, List<string> properties = null, List<string> orderBy = null, string where = null)

List processes

Gets a  list of processes.  An authenticated user will have access to a processes if the user has started the process or if the user is involved in any of the process’s tasks. In a network, only processes that are inside the given network are returned.  In non-network deployments, any authenticated user will see all the process definitions.  If networks are enabled, the network admin can only see the deployments in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListProcessesExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessesApi(config);
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 
            var orderBy = new List<string>(); // List<string> | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  (optional) 
            var where = "where_example";  // string | A string to restrict the returned objects by using a predicate. (optional) 

            try
            {
                // List processes
                ProcessPaging result = apiInstance.ListProcesses(skipCount, maxItems, properties, orderBy, where);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessesApi.ListProcesses: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListProcessesWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List processes
    ApiResponse<ProcessPaging> response = apiInstance.ListProcessesWithHttpInfo(skipCount, maxItems, properties, orderBy, where);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessesApi.ListProcessesWithHttpInfo: " + e.Message);
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

[**ProcessPaging**](ProcessPaging.md)

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

