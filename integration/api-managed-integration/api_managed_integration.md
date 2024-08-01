<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-api-managed-integration",
        "name": "API managed integration",
        "shortDescription": "API-managed integration allows you to provide omni-channel and secure access to business applications that can also hide the complexity of underlying heterogeneous landscapes.",
        "archDiagramLink": "images/API-Managed-Integration_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/API-Managed-Integration.drawio"
        }
    ],

        "tags": "Integration, API, API management, Graph, business data graph, isa-m, sap integration suite, cross use case",
        "category": "Integration"
    }
dc-ref-arch-metadata  -->
![](images/ref-arch-api-managed-integration.png)
<!-- dc-ref-arch-detail-page-start -->
## **API managed integration**
Application Programming Interfaces (APIs) enable integration, interoperability and data sharing between software systems. With the help of an API management solution like the API Management capability within SAP Integration Suite you can provide omni-channel and secure access to solutions. Furthermore, it allows you to enforce usage policies for APIs, controlling API access, analyzing API consumption and more. 
This reference architecture is based on the concepts of the **SAP Integration Solution Advisory Methodology**: Thereof, API managed integration is defined as cross use case pattern. These can complement other integration use case patterns. 

### Flow
The reference architecture diagram shows the runtime perspective for API managed integration covering the integration domains Cloud2Cloud, Cloud2OnPremise and OnPremise2OnPremise. Let’s take a look at the steps in detail:
1. A client application sends out an API call which is intercepted by the API Management capability within SAP Integration Suite which acts as a harmonious protection layer for all API calls that passes its gateway. For this purpose, APIs are exposed as API proxies on API Management which realize a discrete representation of an API entity (an API façade): It abstracts the actual proxy endpoint properties at one end and the actual target. An API proxy includes configuration files, policies, and code snippets to enforce security measures (such as authentication and authorization), transformations (such as modifications of API requests and responses), governance (such as applying throttling, caching) and insights (like monitoring and analytics of API consumption).
   
2. SAP Business Accelerator Hub provides API policy templates, APIs, predefined integration flows and more which can be used to enable interoperability and between API providers and consumers in a protected fashion.
   
Further processing up to the respective API providers (such as an SAP, third-party or custom built solution) depends on the actual use case:

3. Use case "managed API": API requests are forwarded to a data source which acts as an API provider. This use case is suited for integration scenarios which require no or simple transformations and protocol adaptations that can be accomplished with the help of API Management.
   
4. Use case "API managed business data graph": The Graph capability of API Management and allows you to expose business data from SAP business solutions and beyond in the form of a semantically connected data graph. In turn, with the help of Graph you can access data from several data sources via a single unified API. With this use case you can take advantage of a simplified consumption of business data across different data sources realized by a business data graph.

5. Use case "API managed cloud integration": Cloud Integration capability is used whenever advanced mediation and transformation requirements are required that are not supported by API Management.

The API call reaches the respective API provider(s) as follows:

7. If the data source is located on premises (Cloud2OnPremise) it is recommended to use SAP Connectivity service with cloud connector and SAP Destination service to establish a secure connection from SAP BTP to the on-premise landscape.

8. When there is a need (e.g. to meet data compliance and governance requirements) to process data locally you can use the edge integration cell runtime. It is offered as an optional extension to SAP Integration Suite, allowing you to manage APIs and run their integration scenarios within customer-managed private landscapes. Edge integration cell is deployed in customer managed private Kubernetes environments and allows you to design, configure and monitor integrations and APIs in the cloud but run them within your private landscape.

9. In case the integration scenario involves SAP S/4HANA or SAP ECC you can use the SAP Application Interface Framework to enable integration monitoring and error handling for business users.

### Characteristics 
An architecture for API managed integration can be characterized as follows:
- **Governed API consumption**: This allows you to govern the full lifecycle of APIs. It includes the consumption of APIs by enforcing policies, ensuring compliance and control over the integration process.
- **Decoupled integratio**n: With the help of an API façade you can abstract the API from its actual implementation. By doing so, it can enable a decoupled integration between systems, meaning that each system can evolve independently without affecting the others.
- **Advanced protection**: Ensure API security via policies, traffic protection, and compliance.
- Provides visibility and analytical insights: You can centrally collect and analyze API metrics, including option to monetize API consumption.
- **Enables integration and interoperability between software systems**: You can perform transformation and mediations, including a simplified consumption of APIs when using data graphs, to enable interoperability between API providers and consumers.

### Examples in an SAP Context
SAP doesn’t deliver predefined integration scenarios that follow an API managed integration approach. API management solutions are typically implemented by customers or partners. Please find below typical reasons using API managed:
- Achieve a consistent and harmonized omni-channel experience.
- Manage and protect business-critical API assets.
- Simplify integration with SAP and other API providers.	
- Realize revenue in the cloud-native economy.
<!-- dc-ref-arch-detail-page-end -->

### Services and Components
<!-- dc-ref-arch-services-start -->
- [SAP Integration Suite](https://discovery-center.cloud.sap/serviceCatalog/integration-suite?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->
- [SAP Connectivity service](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all)
- [SAP Destination service](https://discovery-center.cloud.sap/serviceCatalog/destination?service_plan=lite&region=all)
<!-- dc-ref-arch-services-end -->

### Resources
<!-- dc-ref-arch-resources-start -->
- [SAP Business Accelerator Hub](https://hub.sap.com)
- [SAP API Management – Overview & Getting started (SAP Community blog post)](https://blogs.sap.com/2016/03/03/sap-api-management-overview-getting-started/)
- [SAP Integration Suite (SAP Help Portal)](https://help.sap.com/docs/integration-suite)
- [SAP Integration Solution Advisory Methodology (SAP Help Portal)](https://help.sap.com/docs/architecture_guidance/f64ada51d9f44c83a751b96f955aad5a/85bcc8675d3e42718279bf7b87dafc2d.html?locale=en-US)
- [SAP Integration Suite (SAP Community topic page)](https://community.sap.com/topics/integration-suite)
<!-- dc-ref-arch-resources-end -->

### Related Missions
<!-- dc-ref-arch-related-missions-start -->
- [Get Started with Integration Suite - API Management](https://discovery-center.cloud.sap/missiondetail/3062/3072/)
- [Create simple, connected digital experiences with API-based integration](https://discovery-center.cloud.sap/missiondetail/3062/3072/)
<!-- dc-ref-arch-related-missions-end -->
