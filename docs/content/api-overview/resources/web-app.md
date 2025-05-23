---
title: "Web App"
date: 2022-04-05T11:05:00-04:00
chapter: false
weight: 22
---

#### Overview
The Web App builder is used to create Azure App Service accounts. It abstracts the Service Plan into the same component, and will also create and configure a linked App Insights resource. If you wish to create a website that connects to an existing service plan or Web App, use the `link_to_service_plan` keyword and provide the resource name of the service plan or Web App to connect to.

* Web Site (`Microsoft.Web/sites`)
* Server Farms (`Microsoft.Web/serverfarms`)
* Source Controls (`Microsoft.Web/sites/sourcecontrols`)
* Application Insights (`Microsoft.Insights/components`)

#### Web App Builder Keywords
| Applies To | Keyword | Purpose |
|-|-|-|
| Web App | name | Sets the name of the web app. |
| Web App | link_to_service_plan | Instructs Farmer to link this webapp to a Farmer service plan configuration defined elsewhere in your application, rather than creating a new one. |
| Web App | link_to_unmanaged_service_plan | Instructs Farmer to link this webapp to an existing service plan that is externally managed, rather than creating a new one. |
| Web App | use_workspace_based_app_insights | Instructs Farmer to use Workspace Based App Insights, which automatically comes with a Log Analytics instance. Both resources will be automatically created. |
| Web App | app_insights_name | Sets the name of the automatically-created app insights instance. |
| Web App | app_insights_off | Removes any automatic app insights creation, configuration and settings for this webapp. |
| Web App | link_to_app_insights | Instructs Farmer to link this webapp to a Farmer App Insights configuration defined elsewhere in your application, rather than creating a new one. |
| Web App | link_to_unmanaged_app_insights | Instructs Farmer to link this webapp to an existing app insights instance that is externally managed, rather than creating a new one. |
| Web App | run_from_package | Sets the web app to use "run from package" deployment capabilities. |
| Web App | website_node_default_version | Sets the node version of the web app. |
| Web App | setting | Sets an app setting of the web app in the form "key" "value". |
| Web App | secret_setting | Sets a "secret" app setting of the web app. You must supply the "key", whilst the value will be supplied as a secure parameter. |
| Web App | settings | Sets a list of app setting of the web app as tuples in the form of ("key", "value"). |
| Web App | connection_string | Creates a connection string whose value is supplied as a secret parameter, or as an ARM expression in the tupled form of ("key", expr), or with the connection string type ("key", expr, SQLAzure). |
| Web App | connection_strings | Creates a set of connection strings of the web app whose values will be supplied as secret parameters. |
| Web App | ftp_state | Allows to enable or disable FTP and FTPS. |
| Web App | https_only | Disables http for this webapp so that only HTTPS is used. |
| Web App | enable_http2 | Configures the webapp to allow clients to connect over http2.0. |
| Web App | disable_client_affinity | Stops the webapp from sending client affinity cookies. |
| Web App | enable_websockets | Configures the webapp to allow clients to connect via websockets. |
| Web App | depends_on | [Sets dependencies for the web app.](../../dependencies/) |
| Web App | docker_image | Sets the docker image to be pulled down from Docker Hub, and the command to execute as a second argument. Automatically sets the OS to Linux. |
| Web App | docker_ci | Turns on continuous integration of the web app from the Docker source repository using a webhook.
| Web App | docker_use_azure_registry | Uses the supplied Azure Container Registry name as the source of the Docker image, instead of Docker Hub. You do not need to specify the full url, but just the name of the registry itself.
| Web App | add_identity | Adds a managed identity to the the Web App. Farmer will automatically set the AZURE_CLIENT_ID application setting to the Client Id of the supplied identity. |
| Web App | keyvault_identity | Adds a managed identity to the the Web App and sets this identity to be used for [KeyVault References](https://docs.microsoft.com/en-us/azure/app-service/app-service-key-vault-references). Farmer will automatically set the AZURE_CLIENT_ID application setting to the Client Id of the supplied identity.  |
| Web App | system_identity | Activates the system identity of the Web App. |
| Web App | enable_cors | Enables CORS support for the app. Either specify `WebApp.AllOrigins` or a list of valid URIs as strings. |
| Web App | enable_cors_credentials | Allows CORS requests with credentials. |
| Web App | source_control | Given a Github repository URI and branch name, configures the web app to automatically deploy those files to the web app |
| Web App | disable_source_control_ci | Disables continuous integration from source control on push |
| Web App | enable_source_control_ci | Enables continuous integration from source control on push |
| Web App | add_extension | Adds the named extension to the Web App |
| Web App | automatic_logging_extension | Enables or disables automatically adding the ASP .NET logging extension for netcore apps (defaults to on unless docker_image is set). |
| Web App | worker_process | Specifies whether to set the web app to 32 or 64 Bitness. |
| Web App | always_on | Sets the "Always On" flag. |
| Web App | add_private_endpoint | Adds a private endpoint for this Webapp to a given subnet |
| Web App | add_private_endpoints | Adds private endpoints for this Webapp to the given subnets |
| Web App | add_slot | Adds a deployment slot to the app |
| Web App | add_slots | Adds multiple deployment slots to the app |
| Web App | health_check_path | Sets the path to your functions health check endpoint, which Azure load balancers will ping to determine which instances are healthy.|
| Web App | custom_domain | Adds a custom domain to the app.  By default this will produce an AppService-managed SSL certificate for your domain as well. Through the overloads of this operator, you can provide a custom certificate thumbprint or choose not to use SSL. You can use this operator multiple times to add multiple custom domains.  |
| Web App | add_allowed_ip_restriction | Adds an 'allow' rule for an ip |
| Web App | add_denied_ip_restriction | Adds a 'deny' rule for an ip |
| Web App | docker_port | Adds `WEBSITES_PORT` setting to map custom docker port to app service port 80 |
| Web App | link_to_vnet | Enable the VNET integration feature in Azure, where all outbound traffic from the web app with be sent via the specified subnet. Use this operator when the given VNET is in the same deployment |
| Web App | link_to_unmanaged_vnet | Enable the VNET integration feature in Azure, where all outbound traffic from the web app with be sent via the specified subnet. Use this operator when the given VNET is *not* in the same deployment |
| Web App | add_virtual_applications | Adds list of `virtualApplication` definitions to the webapp |
| Web App | startup_command | Adds a startup command to be run post-deployment. This is useful on Linux-based web app deployments, where your application is "implicitly" converted into a docker image and may need to be told what to do on startup. |
| App Slot | name | Sets the name for the slot |
| App Slot | add_identity | Sets the user managed identity for the slot. |
| App Slot | system_identity | Sets the system identity to be enabled for the slot. |
| App Slot | keyvault_identity | Sets the identity for accessing key vault. |
| App Slot | setting | Set an arbitrary setting for the slot. |
| App Slot | settings | Sets multiple settings for the slot. |
| App Slot | connection_string | Adds a connection string setting for the slot |
| App Slot | docker_image | Sets the docker image to be pulled down from Docker Hub, and the command to execute as a second argument. This enabled a new container to be staged in a slot. |
| App Slot | add_allowed_ip_restriction | Allows access from this IP when the slot is in production. |
| App Slot | add_denied_ip_restriction | Denies access from this IP when the slot is in production. |
| Service Plan | service_plan_name | Sets the name of the service plan. If not set, uses the name of the web app postfixed with "-plan". |
| Service Plan | runtime_stack | Sets the runtime stack. |
| Service Plan | operating_system | Sets the operating system. |
| Service Plan | sku | Sets the sku of the service plan. |
| Service Plan | worker_size | Sets the size of the service plan worker. |
| Service Plan | number_of_workers | Sets the number of instances on the service plan. |
| Service Plan | zone_redundant | Enables ZoneRedundant on the service plan. |

> **Farmer also comes with a dedicated Service Plan builder** that contains all of the above keywords that apply to a Service Plan.
>
> Use this builder if you wish to have an explicit and clear separation between your web app and service plan. Otherwise, it is recommended to use the service plan keywords that exist directly in the web app builder, and let Farmer handle the connections between them.

#### Post-deployment Builder Keywords
The Web App builder contains special commands that are executed *after* the ARM deployment is completed.

| Keyword | Purpose |
|-|-|
| zip_deploy | Supplying a folder or zip file will instruct Farmer to upload the contents directly to the App Service once the ARM deployment is complete. |
| zip_deploy_slot | Supplying a folder or zip file will instruct Farmer to upload the contents directly to the named slot of the App Service once the ARM deployment is complete. |

#### Configuration Members

| Member | Purpose |
|-|-|
| PublishingPassword | Gets the ARM expression path to the publishing password of this web app. |
| ServicePlan | Gets the Resource Name of the service plan for this web app. |
| AppInsights | Gets the Resource Name of the service plan for the AI resource linked to this web app. |
| SystemIdentity | Gets the system-created managed principal for the web app. It must have been enabled using the system_identity keyword. |

#### Key Vault integration
The Web App builder comes with special integration into KeyVault. By activating KeyVault integration, the web app builder can automatically link to, or even create, a full KeyVault instance. All Secret or ARM Expression-based Settings (e.g. a setting that links to the Key of a Storage Account) will automatically be redirected to KeyVault. The value will be stored in KeyVault and the system identity will be activated and provided into the KeyVault with GET permissions. Lastly, Web App app settings will remain in place, using the Azure App Service built-in KeyVault redirection capabilities.

The following keywords exist on the web app:

| Member | Purpose |
|-|-|
| use_keyvault | Tells the web app to create a brand new KeyVault for this App Service's secrets. |
| link_to_keyvault | Tells the web app to use an existing Farmer-managed KeyVault, which you have defined elsewhere. All secret settings will automatically be mapped into KeyVault. |
| link_to_unmanaged_keyvault | Tells the web app to use an existing non-Farmer managed KeyVault which you have defined elsewhere.  All secret settings will automatically be mapped into KeyVault. |

#### Virtual Applications `virtualApplication`
Virtual applications can be defined for a webapp which allows you to specify alternative directories for the application executables or enable a single web app to host multiple applications at once. By default, the following `virtualApplication` is provided for you:

```fsharp
virtualApplication {
    virtual_path "/"
    physical_path "wwwroot"
}
```

| Keyword                                 | Purpose                                                                  |
| --------------------------------------- | ------------------------------------------------------------------------ |
| virtual_path                            | Provides the virtual path mapping                                        |
| physical_path                           | Specifies the physical directory used (relative to the "site" directory) |
| preloaded                               | Enables the "preload" feature of the virtual application                 |

#### Examples

A basic web application.

```fsharp
open Farmer
open Farmer.Builders
open Farmer.WebApp

let myWebApp = webApp {
    name "myWebApp"
    service_plan_name "myServicePlan"
    setting "myKey" "aValue"
    sku WebApp.Sku.B1
    always_on
    app_insights_off
    worker_size Medium
    number_of_workers 3
    run_from_package
    system_identity
}
```

Using a managed Key Vault instance with automatic secret mapping.

```fsharp
open Farmer
open Farmer.Builders

// Create a basic storage account
let data = storageAccount {
    name "mystorage"
}

// Create a web application with a sensitive setting of storage key and an explicit "secret" setting
// which will be passed through by ARM parameter.
let wa = webApp {
    name "isaac"
    setting "key" "value"
    setting "storagekey" data.Key
    link_to_keyvault (ResourceName "isaacvault")
}

// Create a key vault instance and explicitly grant the web application access to it.
let v = keyVault {
    name "isaacvault"
    add_access_policy (AccessPolicy.create (wa.SystemIdentity.PrincipalId, [ KeyVault.Secret.Get; KeyVault.Secret.List ]))
}
```

Serving two applications simultaneously (a frontend and a backend) from one web app using virtual applications.

```fsharp
open Farmer
open Farmer.Builders

let wa = webApp {
    name "my-site-with-api"
    always_on
    add_virtual_applications [
        virtualApplication {
            virtual_path "/"
            physical_path "frontend"
        }
        virtualApplication {
            virtual_path "/api"
            physical_path "backend"
            preloaded
        }
    ]
}
```
