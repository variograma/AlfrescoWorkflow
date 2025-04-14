# Variograma.AlfrescoWorkflow.Api.DeploymentsApi

All URIs are relative to *http://localhost/alfresco/api/-default-/public/workflow/versions/1*

| Method | HTTP request | Description |
|--------|--------------|-------------|
| [**DeleteDeployment**](DeploymentsApi.md#deletedeployment) | **DELETE** /deployments/{deploymentId} | Delete a deployment |
| [**GetDeployment**](DeploymentsApi.md#getdeployment) | **GET** /deployments/{deploymentId} | Get a deployment |
| [**ListDeployments**](DeploymentsApi.md#listdeployments) | **GET** /deployments | List deployments |

<a id="deletedeployment"></a>
# **DeleteDeployment**
> void DeleteDeployment (string deploymentId)

Delete a deployment

This request will delete the deployment including the tasks, process definitions contained in the deployment.  The request will also delete processes and history information associated with the deployment. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class DeleteDeploymentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new DeploymentsApi(config);
            var deploymentId = "deploymentId_example";  // string | The unique id must be a String. It is returned as an **id** from the entity

            try
            {
                // Delete a deployment
                apiInstance.DeleteDeployment(deploymentId);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling DeploymentsApi.DeleteDeployment: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the DeleteDeploymentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Delete a deployment
    apiInstance.DeleteDeploymentWithHttpInfo(deploymentId);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling DeploymentsApi.DeleteDeploymentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **deploymentId** | **string** | The unique id must be a String. It is returned as an **id** from the entity |  |

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
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="getdeployment"></a>
# **GetDeployment**
> DeploymentEntry GetDeployment (string deploymentId, List<string> properties = null)

Get a deployment

Gets a specified deployment defined by **deploymentId**.  The authenticated user must have role admin (non-network deployments) or network admin (networks enabled).  If networks are enabled, the deployment is only returned if the deployment is in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class GetDeploymentExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new DeploymentsApi(config);
            var deploymentId = "deploymentId_example";  // string | The unique id must be a String. It is returned as an **id** from the entity.
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // Get a deployment
                DeploymentEntry result = apiInstance.GetDeployment(deploymentId, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling DeploymentsApi.GetDeployment: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the GetDeploymentWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // Get a deployment
    ApiResponse<DeploymentEntry> response = apiInstance.GetDeploymentWithHttpInfo(deploymentId, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling DeploymentsApi.GetDeploymentWithHttpInfo: " + e.Message);
    Debug.Print("Status Code: " + e.ErrorCode);
    Debug.Print(e.StackTrace);
}
```

### Parameters

| Name | Type | Description | Notes |
|------|------|-------------|-------|
| **deploymentId** | **string** | The unique id must be a String. It is returned as an **id** from the entity. |  |
| **properties** | [**List&lt;string&gt;**](string.md) | A list of property names. You can use the properties parameter to restrict the number of returned properties. | [optional]  |

### Return type

[**DeploymentEntry**](DeploymentEntry.md)

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
| **404** | **deploymentId** does not exist  |  -  |
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

<a id="listdeployments"></a>
# **ListDeployments**
> DeploymentPaging ListDeployments (int? skipCount = null, int? maxItems = null, List<string> properties = null)

List deployments

Gets a list of deployments.  The authenticated user must have role admin (non-network deployments) or network admin (networks enabled).  If networks are enabled, the network admin can only see the deployments in the given network. 

### Example
```csharp
using System.Collections.Generic;
using System.Diagnostics;
using Variograma.AlfrescoWorkflow.Api;
using Variograma.AlfrescoWorkflow.Client;
using Variograma.AlfrescoWorkflow.Model;

namespace Example
{
    public class ListDeploymentsExample
    {
        public static void Main()
        {
            Configuration config = new Configuration();
            config.BasePath = "http://localhost/alfresco/api/-default-/public/workflow/versions/1";
            // Configure HTTP basic authorization: basicAuth
            config.Username = "YOUR_USERNAME";
            config.Password = "YOUR_PASSWORD";

            var apiInstance = new DeploymentsApi(config);
            var skipCount = 56;  // int? | The number of entities that  exist in the collection before those included in this list. (optional) 
            var maxItems = 56;  // int? | The maximum number of items to return in the list. (optional) 
            var properties = new List<string>(); // List<string> | A list of property names. You can use the properties parameter to restrict the number of returned properties. (optional) 

            try
            {
                // List deployments
                DeploymentPaging result = apiInstance.ListDeployments(skipCount, maxItems, properties);
                Debug.WriteLine(result);
            }
            catch (ApiException  e)
            {
                Debug.Print("Exception when calling DeploymentsApi.ListDeployments: " + e.Message);
                Debug.Print("Status Code: " + e.ErrorCode);
                Debug.Print(e.StackTrace);
            }
        }
    }
}
```

#### Using the ListDeploymentsWithHttpInfo variant
This returns an ApiResponse object which contains the response data, status code and headers.

```csharp
try
{
    // List deployments
    ApiResponse<DeploymentPaging> response = apiInstance.ListDeploymentsWithHttpInfo(skipCount, maxItems, properties);
    Debug.Write("Status Code: " + response.StatusCode);
    Debug.Write("Response Headers: " + response.Headers);
    Debug.Write("Response Body: " + response.Data);
}
catch (ApiException e)
{
    Debug.Print("Exception when calling DeploymentsApi.ListDeploymentsWithHttpInfo: " + e.Message);
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

### Return type

[**DeploymentPaging**](DeploymentPaging.md)

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
| **0** | Unexpected error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

