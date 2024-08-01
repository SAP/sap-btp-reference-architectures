<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-master-data-integration",
        "name": "Master data integration",
        "shortDescription": "With the help of master data integration, you can share replicate master data objects across connected business applications.",
        "archDiagramLink": "images/Master-Data-Integration_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Master-Data-Integration.drawio"
        }
    ],

        "tags": "Integration , sap integration suite, sap master data integration, mdi, isa-m, process integration style, cloud2cloud, cloud integration, master data integration",
        "category": "Integration"
    }
dc-ref-arch-metadata  -->
![](images/ref-arch-master-data-integration.png)
<!-- dc-ref-arch-detail-page-start -->
## **Master data integration**
With the help of master data integration, you can replicate master data objects across connected business applications. Master data is basic data about business-relevant objects that is required in different contexts, such as materials or business partners. For ensuring data consistency, the master data is synchronized across connected business applications in (near) real time fashion using APIs.

This reference architecture is based on the concepts of the **SAP Integration Solution Advisory Methodology**: Thereof, master data integration is defined as an integration use case pattern which belongs to the process integration style. The diagram shows the runtime perspective for A2A integration covering the integration domains Cloud2Cloud, Cloud2OnPremise and OnPremise2OnPremise.

### Flow

Let’s take a look at the steps in detail:
1. SAP cloud solutions which are supported by SAP Master Data Integration (see [Integration](https://help.sap.com/docs/master-data-integration/sap-master-data-integration-prod/integration?locale=en-US)) synchronize their master data with SAP Master Data Integration. In this context a solution can act as a master data provider which sends master data change requests toward SAP Master Data Integration. Or it can act as a master data consumer which receives master data change events from SAP Master Data Integration. These events are exchanged asynchronously using REST or SOAP based APIs (the latter one for business partner master data only).
   
2. All master changes are stored centrally in the master data event log of SAP Master Data Integration and shared with master data consumers using a distribution model. The main benefit of using SAP Master Data Integration is that you can implement a central master data hub which allows connected solutions to synchronize their local master data databases with the master data database of the central hub in an efficient and scalable fashion.
   
3. The Cloud Integration capability within SAP Integration Suite is used for master data integration scenarios between SAP solutions which are not yet supported by SAP Master Data Integration. When you have already implemented master data integration scenarios using Cloud Integration which are supported by SAP Master Data Integration in the meantime, you may continue using those as unless you want to take advantage of SAP Master Data Integration’s benefits.
   
4. SAP Business Accelerator Hub provides predefined integration flows and also APIs, adapters and more to build custom integration flows which are deployed on Cloud Integration.
   
5. When exchanging master data between SAP Master Data Integration and a third-party solution (cloud, on-premise) or SAP on premise solution (with the exception of newer release of SAP S/4HANA) you use Cloud Integration, too: It includes an SAP Master Data Integration adapter to synchronize master data with SAP Master Data Integration.
    
6. In case of on-premise solutions it is recommended to also use SAP Connectivity service with Cloud Connector and Destination service for establishing a secure connection from SAP BTP to the on-premise landscape.
   
7. Higher release versions of SAP S/4HANA can also synchronize their master data with SAP Master Data Integration (without Cloud Integration).
   
8. In case the integration scenario involves SAP S/4HANA (or SAP ECC) the SAP Application Interface Framework can enable integration monitoring and error handling for business users.
    
If you are looking to implement master data management processes such as consolidation, data quality control, and central governance you may additionally use SAP Master Data Governance solution which enables such functionality. Regarding the reference architecture for master data: SAP Master Data Governance acts as a master data provider or master data consumer and can integrate with SAP Master Data Integration for selected scenarios, too.

### Characteristics
An architecture for master data integration can be characterized as follows:
- **Master data synchronization**: Ability to synchronize master data objects between diverse solutions which can act as master data provider and/or master data consumer system. Data synchronization aims at ensuring data consistency across a solution landscape.
- **Data transformation and harmonization**: Support of (structure and value) mappings of master data from various sources. Ideally this includes a unified representation of master data across connected solutions.
- **(Near) Real-time processing**: A (near-) real-time processing is needed to enable consistent and up-to-date availability of master data information across the organization.
- **Data security and privacy**: Ability to meet data security and compliance regulations. These include for instance the protection of sensitive data, compliant data distribution to ensure data confidentiality and integrity.

### Examples in an SAP Context
SAP delivers predefined master data integration scenarios along end-to-end business processes spanning across multiple SAP solutions. The following examples are using the SAP Master Data Integration service for synchronizing master data:
- Synchronization of the workforce person master data object between SAP S/4HANA Cloud and SAP SuccessFactors HXM Suite as part of the [Hire to Retire process (for cloud deployment)](https://api.sap.com/dfd/HR1C1-DFDDataFlowsforHRData)
- Synchronization of the cost center master data object as part of the [Source to Pay process (for cloud deployment)](https://api.sap.com/dfd/SP1C1-DFDMasterDataFlows)
- Synchronization of the customer master data object as part of the [Lead to Cash process (for cloud deployment)](https://api.sap.com/dfd/LC1C1-DFDMasterDataFlowforBusinessPartnerCustomer)
  
### Reasonable Alternatives
For selected SAP lines-of-business solutions further integration technologies are available which are tailored to the needs of the respective business solution: 
- [SAP Integration Suite, managed gateway for spend management and SAP Business Network](https://help.sap.com/docs/sisgw?locale=en-US): This solution, which is formerly known as SAP Ariba Cloud Integration Gateway, is based on SAP Integration Suite. This managed gateway facilitates the integration of buyers' and suppliers' SAP ERP or SAP S/4HANA systems with intelligent spend solutions from SAP and SAP Business Network. Managed gateway includes self-service wizards for configuring predefined integration scenarios, automated testing, and real-time monitoring.
  
    You use the managed gateway for such predefined integration scenarios that are that are not supported by SAP Master Data Integration yet. For more information about integration scenarios that are supported by the managed gateway see [overview guide for buyers](https://help.sap.com/docs/ARIBA_CIG/1b1724b5f3e248568430b640c0412c24/dabf918d862847728f00d80025e38f28.html?locale=en-US) and [overview guide for suppliers](https://help.sap.com/docs/ARIBA_CIG/791693e960f6494b8ea0a0bae07d406c/f13af7d9e5ea4bee9afb40249063833d.html?locale=en-US).
<!-- dc-ref-arch-detail-page-end -->

### Services and Components
<!-- dc-ref-arch-services-start -->
- [SAP Integration Suite](https://discovery-center.cloud.sap/serviceCatalog/integration-suite?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->
- [SAP Master Data Integration](https://discovery-center.cloud.sap/serviceCatalog/master-data-integration?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->
- [SAP Connectivity service](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all)
- [SAP Destination service](https://discovery-center.cloud.sap/serviceCatalog/destination?service_plan=lite&region=all)
<!-- dc-ref-arch-services-end -->
  
### Resources
<!-- dc-ref-arch-resources-start -->
- [SAP Business Accelerator Hub](https://hub.sap.com)<!-- dc-res-metadata: {"description": "This hub is a central catalog which is hosted by SAP and allows you to discover, explore, test and consume different types of digital content such as APIs, events, integration content, adapters to accelerate integration and extension of SAP solutions."} dc-res-metadata -->: This hub is a central catalog which is hosted by SAP and allows you to discover, explore, test and consume different types of digital content such as APIs, events, integration content, adapters to accelerate integration and extension of SAP solutions.
  
- SAP Help Portal:
    - [SAP Application Interface Framework](https://help.sap.com/docs/SAP_APLICATION_INTERFACE_FRAMEWORK_OVERVIEW)<!-- dc-res-metadata: {"description": ": This technology is used together with SAP ECC or SAP S/4HANA, to  develop and monitor interfaces as well as execute error handling within the SAP backend system."} dc-res-metadata -->: This technology is used together with SAP ECC or SAP S/4HANA, to  develop and monitor interfaces as well as execute error handling within the SAP backend system.
    - [SAP Integration Suite](https://help.sap.com/docs/integration-suite)
    - [SAP Master Data Integration](https://help.sap.com/docs/SAP_MASTER_DATA_INTEGRATION)
    - [SAP Integration Solution Advisory Methodology](https://help.sap.com/docs/architecture_guidance/f64ada51d9f44c83a751b96f955aad5a/85bcc8675d3e42718279bf7b87dafc2d.html?locale=en-US)
      
- SAP Community:
    - [SAP Integration Suite (topic page)](https://community.sap.com/topics/integration-suite)
    - [SAP Master Data Integration – sharing and synchronizing master data in the integrated Intelligent Suite (blog post)](https://blogs.sap.com/2020/07/21/sap-cloud-platform-master-data-integration-sharing-and-synchronizing-master-data-in-the-integrated-intelligent-suite/)
    - [SAP Integration Suite – Integration with SAP Master Data Integration (MDI) service (blog post)](https://blogs.sap.com/2022/05/20/sap-integration-suite-integration-with-sap-master-data-integration-mdi-service/) 
    - [Master Data Integration and Master Data Management: What’s the Difference (blog post)](https://blogs.sap.com/2020/10/23/master-data-integration-and-master-data-management-whats-the-difference/)

<!-- dc-ref-arch-resources-end -->
  
### Related Missions
<!-- dc-ref-arch-related-missions-start -->
- [Use SAP Integration Suite to Synchronize Master Data](https://discovery-center.cloud.sap/missiondetail/4248/4505/)
- [Get started with SAP Integration Suite](https://discovery-center.cloud.sap/missiondetail/3258/3327/)
- [S/4HANA Cloud - Cost Center Mass Update](https://discovery-center.cloud.sap/missiondetail/3419/3459/)
<!-- dc-ref-arch-related-missions-end -->

