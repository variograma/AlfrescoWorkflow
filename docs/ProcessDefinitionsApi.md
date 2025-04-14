# Variograma.AlfrescoWorkflow.Api.ProcessDefinitionsApi

All URIs are relative to *http://localhost/alfresco/api/-default-/public/workflow/versions/1*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**GetProcessDefinition**](ProcessDefinitionsApi.md#getprocessdefinition) | **GET** /process-definitions/{processDefinitionId} | Get a process definition |
| [**GetProcessDefinitionImage**](ProcessDefinitionsApi.md#getprocessdefinitionimage) | **GET** /process-definitions/{processDefinitionId}/image | Get a process definition image |
| [**GetProcessDefinitionStartFormModel**](ProcessDefinitionsApi.md#getprocessdefinitionstartformmodel) | **GET** /process-definitions/{processDefinitionId}/start-form-model | Get a start form model |
| [**ListProcessDefinitions**](ProcessDefinitionsApi.md#listprocessdefinitions) | **GET** /process-definitions | List process definitions |

<a id="getprocessdefinition"></a>
# **GetProcessDefinition**
> ProcessDefinitionEntry GetProcessDefinition (string processDefinitionId, List<string> properties = null)

Get a process definition

Gets a process definition identified by **processDefinitionId**.  In non-network deployments, any authenticated user will see all the process definitions. If networks are enabled, the network admin can only see the deployments in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetProcessDefinitionExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessDefinitionsApi(config);
            var processDefinitionId = "processDefinitionId_example";  // string | The identifier of a process definition.
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a process definition
                ProcessDefinitionEntry result = apiInstance.GetProcessDefinition(processDefinitionId, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinition: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProcessDefinitionWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a process definition
    ApiResponse<ProcessDefinitionEntry> response = apiInstance.GetProcessDefinitionWithHttpInfo(processDefinitionId, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinitionWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processDefinitionId** | **string** | The identifier of a process definition. |  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**ProcessDefinitionEntry**](ProcessDefinitionEntry.md)

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
| **404** | **processDefinitionId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprocessdefinitionimage"></a>
# **GetProcessDefinitionImage**
> System.IO.Stream GetProcessDefinitionImage (string processDefinitionId)

Get a process definition image

Gets an image that represents a single process definition identified by **processDefinitionId**.  In non-network deployments, any authenticated user will see all the process definitions.  If networks are enabled, the network admin can only see the deployments in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetProcessDefinitionImageExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessDefinitionsApi(config);
            var processDefinitionId = "processDefinitionId_example";  // string | The identifier of a process definition.

            try
            {
                // Get a process definition image
                System.IO.Stream result = apiInstance.GetProcessDefinitionImage(processDefinitionId);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinitionImage: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProcessDefinitionImageWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a process definition image
    ApiResponse<System.IO.Stream> response = apiInstance.GetProcessDefinitionImageWithHttpInfo(processDefinitionId);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinitionImageWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processDefinitionId** | **string** | The identifier of a process definition. |  |

### Return type

**System.IO.Stream**

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json, image/png


### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Successful response |  -  |
| **401** | Authentication failed |  -  |
| **404** | **processDefinitionId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getprocessdefinitionstartformmodel"></a>
# **GetProcessDefinitionStartFormModel**
> TaskFormModelPaging GetProcessDefinitionStartFormModel (string processDefinitionId, List<string> properties = null)

Get a start form model

Gets a model of the start form type definition.  An authenticated user will have access to all start form models. In a network, only start form models that are inside the given network are returned. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetProcessDefinitionStartFormModelExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessDefinitionsApi(config);
            var processDefinitionId = "processDefinitionId_example";  // string | The identifier of a process definition.
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a start form model
                TaskFormModelPaging result = apiInstance.GetProcessDefinitionStartFormModel(processDefinitionId, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinitionStartFormModel: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetProcessDefinitionStartFormModelWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a start form model
    ApiResponse<TaskFormModelPaging> response = apiInstance.GetProcessDefinitionStartFormModelWithHttpInfo(processDefinitionId, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessDefinitionsApi.GetProcessDefinitionStartFormModelWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **processDefinitionId** | **string** | The identifier of a process definition. |  |
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
| **401** | Authentication failed |  -  |
| **404** | **processDefinitionId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listprocessdefinitions"></a>
# **ListProcessDefinitions**
> ProcessDefinitionPaging ListProcessDefinitions (int? skipCount = null, int? maxItems = null, List<string> properties = null, List<string> orderBy = null, string where = null)

List process definitions

Gets a list of process definitions.  In non-network deployments, any authenticated user will see all the process definitions.  If networks are enabled, the network admin can only see the deployments in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListProcessDefinitionsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new ProcessDefinitionsApi(config);
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 
            var orderBy = new List<string>(); // List<string> | A string to control the order of the entities returned in a list. You can use the **orderby** parameter to sort the list by one or more fields.  Each field has a default sort order, which is normally ascending order. Read the API method implementation notes above to check if any fields used in this method have a descending default search order.  To sort the entities in a specific order, you can use the **ASC** and **DESC** keywords for any field.  (optional) 
            var where = "where_example";  // string | A string to restrict the returned objects by using a predicate. (optional) 

            try
            {
                // List process definitions
                ProcessDefinitionPaging result = apiInstance.ListProcessDefinitions(skipCount, maxItems, properties, orderBy, where);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling ProcessDefinitionsApi.ListProcessDefinitions: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListProcessDefinitionsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List process definitions
    ApiResponse<ProcessDefinitionPaging> response = apiInstance.ListProcessDefinitionsWithHttpInfo(skipCount, maxItems, properties, orderBy, where);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling ProcessDefinitionsApi.ListProcessDefinitionsWithHttpInfo: " + e.Message);
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

[**ProcessDefinitionPaging**](ProcessDefinitionPaging.md)

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

