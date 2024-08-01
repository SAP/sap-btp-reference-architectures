<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-application-integration",
        "name": "Application to application integration",
        "shortDescription": "With the help of application-to-application (A2A) integration you can exchange transactional data along internal company processes by connecting involved business applications in a (near-) real-time fashion.",
        "archDiagramLink": "images/Application-to-Application-Integration_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Application-to-Application-Integration.drawio"
        }
    ],

        "tags": "Integration, A2A integration, isa-m, application integration",
        "category": "Integration"
    }
dc-ref-arch-metadata  -->
![](images/ref-arch-a2a-integration.png)
<!-- dc-ref-arch-detail-page-start -->
## **Application-to-application integration**
With the help of application-to-application (A2A) integration you can exchange transactional data along internal company processes by connecting involved business applications in a (near-) real-time fashion. Messages are used for exchanging transactional data which trigger the execution of the next process step in a connected business solution. Transactional data refers to data about ongoing business activities such as physical goods movement or sales order documents. This reference architecture is based on the concepts of the **SAP Integration Solution Advisory Methodology**: Thereof, A2A integration is defined as an integration use case pattern which belongs to the process integration style. The diagram shows the runtime perspective for A2A integration covering the integration domains Cloud2Cloud, Cloud2OnPremise and OnPremise2OnPremise.

### Flow
In the following the message flow for application-to-application integration is outlined:
1. An SAP or third-party cloud solution issues transactional data as messages. The transactional data is sent out as a message which is a package of data comprising out of a header and a payload. Typically, the message header contains information such as the logical or physical receiver of the message and the payload contains the actual business data.
   
3. Direct exchange of messages is possible whenever the outbound API of the sending solution and the inbound API of the receiving solution are aligned with regards to the API definition (such as schema, transport protocol). This option is available for selected SAP integration scenarios and is suited for simple landscapes only. You can also use the direct integration option for custom-build or partner solutions if these are also based on aligned APIs.
   
5. In case of unaligned APIs between a sending and one or more receiving solutions (Cloud2Cloud, Cloud2OnPremise) the Cloud Integration capability within SAP Integration Suite is used. It applies required mediations (such as receiver determinations, filtering, aggregations) and transformations (such as structure and value mappings, protocol conversion) to enable an interoperability between the sending and receiving solution(s). You can also Cloud Integration for integration scenarios that are based on aligned APIs by generating route-through integration flows. When using Cloud Integration, you can benefit from a decoupled integration of solutions, error handling and more.
   
7. SAP Business Accelerator Hub provides predefined integration flows which you configure and deploy on Cloud Integration. The hub includes also a catalogue of APIs, adapters and more which you can use for developing custom integration flows.
   
9. Whenever the integration scenario involves an on-premise solution (Cloud2OnPremise) it is recommended to use the SAP Connectivity service with cloud connector and SAP Destination service to establish a secure connection from SAP BTP to the on premise landscape.
    
11. When there is a need (e.g. to meet data compliance and governance requirements) to process data locally you can use the edge integration cell runtime. It is offered as an optional extension to SAP Integration Suite, allowing you to manage APIs and run their integration scenarios within customer-managed private landscapes. Edge integration cell is deployed in customer managed private Kubernetes environments and allows you to design, configure and monitor integrations and APIs in the cloud but run them within your private landscape, see [Edge Integration Cell (design-, runtime and operations view)](https://discovery-center.cloud.sap/githubrefarch/SAP/sap-btp-reference-architectures/main/integration/application-to-application-integration/add-images/A2A-Edge-Integration-Cell_diagram.png).
    
13. In case the integration scenario involves SAP S/4HANA or SAP ECC you can use the SAP Application Interface Framework to enable integration monitoring and error handling for business users.

### Characteristics

- **Use of asynchronous communication**: This is the preferred communication method for most A2A integration scenarios which eliminates a tight coupling between business applications and increases resilience. For this purpose, you use SOAP, REST or OData which support asynchronous communication. You use synchronous communication only if your business scenario requires a synchronous processing (example: Availability to promise check of stock for planned orders).
- **Based on directed messages**: Such a message type is used to exchange transactional data between sending and receiving solutions. Directed means that the sender addresses one or more receivers which are determined either within the sending system (logical receiver) or within the integration technology (physical receiver).
- **Support of exception handling**: There are many reasons why exceptions occur, for instance unavailability of a receiving solution, incorrect message content, improper configuration settings. As a result, the transmission of messages will fail which require a proper exception handling.
- **Ensure transport- and message-level security**: For enabling transport-level security it is recommended to use secured communication whenever data is exchanged over the public internet. For message-level security you use digital encryption and signatures in order to protect the content of messages that are exchanged between solutions.

### Examples in an SAP Context
SAP delivers predefined A2A integration scenarios along end-to-end business processes spanning across multiple SAP business applications. Here are some examples:
- Exchange of sales orders between SAP Commerce Cloud and SAP S/4HANA as part of the [Lead-to-Cash process (for cloud deployment)](https://api.sap.com/dfd/LC1C1-DFDTransactionalDataFlows)
- Replicate service entry sheets or timesheets from SAP Fieldglass Vendor Management System to SAP S/4HANA as part of the [External Workforce process (for cloud deployment)](https://api.sap.com/dfd/EW1H1-DFDTransactionalDataFlows)
- Exchange of maintenance orders between SAP S/4HANA and SAP Service and Asset Manager) as part of the [Acquire-to-Decommission process (for hybrid deployment)](https://api.sap.com/dfd/AD1H2-DFDDataFlows)

### Reasonable Alternatives
For selected SAP lines-of-business solutions further integration technologies are available which are tailored to the needs of the respective business solution:

- [SAP Integration Suite, managed gateway for spend management and SAP Business Network](https://help.sap.com/docs/sisgw?locale=en-US): This solution, which is formerly known as SAP Ariba Cloud Integration Gateway, is based on SAP Integration Suite. This managed gateway facilitates the integration of buyers' and suppliers' SAP ERP or SAP S/4HANA systems with intelligent spend solutions from SAP and SAP Business Network. Managed gateway includes self-service wizards for configuring predefined integration scenarios, automated testing, and real-time monitoring. If you already have SAP Integration Suite in place you can also reuse mappings of managed gateway to run same integration scenarios on Cloud Integration, for details see: [Content Transformation Service](https://help.sap.com/docs/sisgw/sap-ariba-cloud-integration-gateway-installation-guide/content-transformation-as-service?locale=en-US).
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
- [SAP Application Interface Framework](https://help.sap.com/docs/SAP_APPLICATION_INTERFACE_FRAMEWORK_OVERVIEW)
- [SAP Integration Suite (SAP Help Portal)](https://help.sap.com/docs/integration-suite)
- [SAP Integration Solution Advisory Methodology (SAP Help Portal)](https://help.sap.com/docs/integration-suite)
- [SAP Integration Suite (SAP Community topic page)](https://community.sap.com/topics/integration-suite)
<!-- dc-ref-arch-resources-end -->

### Related Missions
<!-- dc-ref-arch-related-missions-start -->
- [Get started with SAP Integration Suite](https://discovery-center.cloud.sap/missiondetail/3258/3327/)
- [Publish Documents from SAP S/4HANA Cloud to SharePoint](https://discovery-center.cloud.sap/missiondetail/3324/3365/)
- [Extract your Ariba Spend Data using SAP Integration Suite](https://discovery-center.cloud.sap/missiondetail/4038/4245/)

<!-- dc-ref-arch-related-missions-end -->
