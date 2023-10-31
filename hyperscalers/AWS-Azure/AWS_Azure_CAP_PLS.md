<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-AWS-Azure-CAP-PLS",
        "name": "Secure Connectivity with SAP Private Link service",
        "shortDescription": "The reference architecture demonstrates how SAP Private Link service can be used to securely communicate with an SAP S/4HANA system deployed in a customer-managed Microsoft Azure or AWS account from SAP BTP, Cloud Foundry environment.",
        "archDiagramLink": "images/generic-privatelink.png",
        "tags": "Hyperscaler",
        "category": "Hyperscaler"
    }
dc-ref-arch-metadata  -->
<!-- dc-ref-arch-detail-page-start -->
## **Secure Connectivity with SAP Private Link service**

Private Link Service is a feature offered by cloud providers like Microsoft Azure and Amazon Web Services (AWS) that allows customers to expose their services in their virtual networks to consumers in other virtual networks or subscriptions. The primary goal of Private Link Service is to ensure that data offered by service providers is only accessible through a private endpoint, which ensures that the data doesn't traverse over the public internet.

SAP Private Link Service service allows to securely connect applications running on SAP BTP to workloads running on hyperscalers. This ensures that traffic is not routed through the public internet but stays within the hyperscaler infrastructure. This helps to minimize attack vectors and ensures secure communication between SAP BTP and hyperscaler workload. To use Private Link Service, service providers would set up a standard Load Balancer in front of their service in Azure and then enable Private Link Service on one or more standard public IP addresses. Consumers, on the other hand, would create a private endpoint in their virtual network and connect it to the service provider's service.

More details about [SAP Private Link Service ](https://help.sap.com/docs/PRIVATE_LINK?locale=en-US).

### Flow
To establish the private connection, you first need create a service instance of the SAP Private Link service by providing the identifier of the IaaS provider service instance. After approving the creation of the private endpoint in your IaaS provider account, you bind the service instance to your application and can then start using the private endpoint.

However, this binding does not include any credentials for accessing the service in your own IaaS account. You need to provide the credentials to your application by different means, for example, by creating a user-provided service that contains the required information, and binding it to the application.

**Service Identifier**: The unique identifier of a service instance of an IaaS provider service that has to be provided during the creation of the SAP Private Link service instance. The actual term depends on the IaaS provider, for example, in Azure, this unique service identifier is called service resource.
   
**Service Instance**: Creating a service instance of the SAP Private Link service sets up a private endpoint that is associated with this service instance.

**Binding**: Binding the service instance of the SAP Private Link service to the application gives the Cloud Foundry space access to the private endpoint. Binding the user-provided service to the application shares the service credentials with the application.

**Credentials**: Creating a user-provided service, for example, enables you to share the credentials of the bound service instance in the IaaS provider account with the application in your SAP BTP account.

### Characteristics
Currently SAP Private Link service supports private endpoints on Microsoft Azure and Amazon Web Services. Supported services from each of the vendors are as follows:
- [Supported Microsoft Azure services](https://help.sap.com/docs/private-link/private-link1/consume-azure-services-in-sap-btp): To privately access a service in your Azure subcription, SAP Private Link service creates a private endpoint and reuses the private link functionality of Azure. 
- [Supported AWS services](https://help.sap.com/docs/private-link/private-link1/consume-amazon-web-services-in-sap-btp): To privately access a service in your AWS subcription, SAP Private Link service creates a private endpoint and reuses the private link functionality of AWS. 

### Examples in an SAP Context
The most commonly used use case for SAP Private Link service is to communicate with an SAP S/4HANA system or other SAP or non-SAP systems running on a VM in your own Microsoft Azure or AWS account privately from within SAP BTP, Cloud Foundry environment.

This connection can be established by creating a hyperscaler Endpoint Service that exposes a Load Balancer which routes traffic to the SAP S/4HANA system. The service name of that Endpoint Service must then be used to create an SAP Private Link service instance. As soon as the connection is established successfully, the SAP Private Link service provides a private hostname pointing to your Endpoint Service.

You can also find an end-to-end SAP S/4HANA extension use case with step-by-step instructions, both for AWS and Azure, in this use case titled [Enhance core ERP business processes with resilient applications on SAP BTP](https://github.com/SAP-samples/btp-build-resilient-apps).

The second use case is to use the service name of one of the supported services offered by AWS instead of a custom service name. The basic functionality is the same, but instead of a connection to a custom endpoint exposed via an AWS Endpoint Service, the connection will be established to a service natively provided by AWS, such as the Amazon Simple Queue Service.

<!-- dc-ref-arch-detail-page-end -->

### BTP services / SAP solutions
<!-- dc-ref-arch-services-start -->

The reference architecture for SAP S/4HANA extensibility using SAP Private Link service uses the following SAP BTP services:

- [SAP Private Link Service](https://discovery-center.cloud.sap/serviceCatalog/private-link-service?service_plan=standard&region=all&commercialModel=cloud): SAP Private Link service establishes a private connection between selected SAP BTP services and selected services in your own IaaS provider accounts. By reusing the private link functionality of our partner IaaS providers, it lets you access your services through private network connections to avoid data transfer via the public Internet.
  
- [SAP Business Application Studio](https://discovery-center.cloud.sap/serviceCatalog/business-application-studio?region=all): SAP Business Application Studio (the next generation of SAP Web IDE) is a powerful and modern development environment, tailored for efficient development of business applications for the Intelligent Enterprise. Available as a cloud service, it provides developers a desktop-like experience similar to market leading IDEs, while accelerating time-to-market with high-productivity development tools such as wizards and templates, graphical editors, quick deployment, and more.

- [SAP Event Mesh](https://discovery-center.cloud.sap/serviceCatalog/event-mesh?region=all): SAP Event Mesh allows applications to communicate through asynchronous events.

- [SAP Build Work Zone, Standard Edition](https://discovery-center.cloud.sap/serviceCatalog/sap-build-work-zone-standard-edition?region=all): SAP Build Work Zone, standard edition enables organizations to establish a unified point of access to SAP (e.g. SAP S/4HANA), custom-built, and third party applications and extensions, both on the cloud and on premise. 

- [SAP Continuous Integration and Delivery](https://discovery-center.cloud.sap/serviceCatalog/continuous-integration--delivery?region=all): SAP Continuous Integration and Delivery lets you configure and run predefined continuous integration and delivery (CI/CD) pipelines that automatically build, test, and deploy your code changes to speed up your development and delivery cycles.

- [SAP Cloud Transport Management](https://discovery-center.cloud.sap/serviceCatalog/cloud-transport-management?region=all): SAP Cloud Transport Management service lets you manage software deliverables between accounts of different environments (such as Cloud Foundry, ABAP, and Neo), by transporting them across various runtimes. This includes application artifacts as well as their respective application-specific content.

- [SAP HANA Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-hana-cloud?region=all): SAP HANA Cloud is a database-as-a-service that powers mission-critical applications and real-time analytics with one solution at petabyte scale. Converge relational, graph, spatial, and document store and develop smart applications with embedded machine learning. Process mission-critical data at proven in-memory speed and manage it more efficiently with integrated multi-tier storage.

- [SAP BTP, Cloud Foundry Runtime](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime?region=all): The SAP BTP, Cloud Foundry runtime lets you develop polyglot cloud-native applications and run them on the SAP BTP Cloud Foundry environment.

- [Destination](https://discovery-center.cloud.sap/serviceCatalog/destination?service_plan=lite&region=all&commercialModel=cloud): The Destination service lets you retrieve the backend destination details you need to configure applications in the Cloud Foundry environment.

- [SAP HTML5 Application Repository Service for SAP BTP](https://discovery-center.cloud.sap/serviceCatalog/html5-application-repository-service?region=all): The HTML5 Application Repository service for SAP BTP enables central storage of HTML5 applications on SAP BTP. The service allows application developers to manage the lifecycle of their HTML5 applications. In runtime, the service enables the consuming application, typically the application router, to access HTML5 application static content in a secure and efficient manner.

- [SAP Application Logging Service for SAP BTP](https://discovery-center.cloud.sap/serviceCatalog/application-logging-service?region=all): The SAP Application Logging service for SAP BTP lets you stream logs of bound Cloud Foundry applications to a central application logging stack. SAP Application Logging service for SAP BTP uses Elastic Stack to store and visualize your application log data.

- [SAP Authorization and Trust Management Service](https://discovery-center.cloud.sap/serviceCatalog/authorization-and-trust-management-service?region=all): The SAP Authorization and Trust Management service lets you manage user authorizations and trust to identity providers. Identity providers are the user base for applications. We recommend that you use an IAS identity authentication tenant, an SAP on-premise system, or a custom corporate identity provider.

- [Application Autoscaler](https://discovery-center.cloud.sap/serviceCatalog/application-autoscaler?service_plan=standard&region=all&commercialModel=cloud): Application Autoscaler lets you automatically increase or decrease the number of your application instances based on the policies you have defined.

<!-- dc-ref-arch-services-end -->

### Resources
<!-- dc-ref-arch-resources-start -->
For more information about the different technologies used as part of this reference architecture you may check out the following resources:

- Documentation: [SAP Private Link Service](https://help.sap.com/docs/private-link)
- Documentation: [Azure Private Link](https://azure.microsoft.com/en-us/products/private-link)
- Documentation: [AWS PrivateLink](https://aws.amazon.com/privatelink/)
- Blog post: [Extend your Business Processes with the new SAP Private Link service](https://blogs.sap.com/2022/06/03/extend-your-business-processes-with-the-new-sap-private-link-service/)
- Blog post: [SAP Private Link in Action: How FrieslandCampina safeguards their integration flows with Azure Storage Account](https://blogs.sap.com/2023/04/07/sap-private-link-in-action-how-frieslandcampina-safeguards-their-integration-flows-with-azure-storage-account/)
- Blog post: [SAP Private Link service use cases for SAP Cloud Integration and SAP Build Work Zone, Standard Edition](https://blogs.sap.com/2022/08/22/sap-private-link-service-use-cases-for-sap-cloud-integration-and-sap-launchpad/)
- Blog post: [SAP Private linky swear with Azure – running Cloud Connector and SAP Private Link side-by-side](https://blogs.sap.com/2022/07/07/btp-private-linky-swear-with-azure-running-cloud-connector-and-sap-private-link-side-by-side/)
- GitHub: [Enhance core ERP business processes with resilient applications on SAP BTP](https://github.com/SAP-samples/btp-build-resilient-apps/blob/main/tutorials/05_setupconnectivity/privatelink.md)
- GitHub: [SAP Private Link Service Use Cases for SAP Cloud Integration and SAP Build Work Zone, Standard Edition](https://github.com/SAP-samples/btp-private-link-approuter)
- Tutorial: [Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/mission.private-link-connect.html)
- Tutorial: [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html)

<!-- dc-ref-arch-resources-end -->

### Related Missions and Tutorials
<!-- dc-ref-arch-related-missions-start -->
If you would like to implement solutions that are related to this reference architecture and technologies used you may continue with the following SAP Discovery Center missions:
- [Enhance core ERP business processes with resilient applications on SAP BTP](https://discovery-center.cloud.sap/missiondetail/3501/3542/)
- [Build Events-to-Business Actions Apps with SAP BTP and MS Azure/AWS](https://discovery-center.cloud.sap/missiondetail/4172/4422/)
- [Enable Supplier Collaboration across SAP and Microsoft Azure Ecosystem using SAP BTP](https://discovery-center.cloud.sap/missiondetail/4068/4280/)
  
<!-- dc-ref-arch-related-missions-end -->