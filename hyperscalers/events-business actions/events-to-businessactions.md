<!-- [IMPORTANT] Do not remove the comments below. These comments are necessary for importing the content to DC -->

<!-- dc-ref-arch-metadata : 
    {
        "id": "Small cased alphanumeric unique identified. Max 255 characters. E.g.: ref-archmaster-data-integration",
        "name": "Public name as shown in catalog view.  Max 255 characters. E.g.: Master Data Integration",
        "shortDescription": "Public short description as shown in catalog view.  Max 255 characters. E.g.: With the help of master data integration, you can share replicate master data objects across connected business applications.",
        "archDiagramLink": "Relative path to image. Max 1024 characters. E.g.: images/ref-arch-master-data-integration.png",
        "tags": "Comma separated string; With or without space (follow any 1 throughout). Used for search & search engine optimization (invisible in DC). Max 1024 characters. E.g.: Integration , sap integration suite, isa-m",
        "category": "Category to which the ref arch belongs. Avaiable categories - Integration, Hyperscaler, Data Analytics"
    }
dc-ref-arch-metadata  -->

<!-- dc-ref-arch-detail-page-start -->
## Events to Business Actions Framework

An event-driven framework is an extension application on SAP BTP for the execution of SAP business workflows triggered by events. This enables us to construct event orchestration from any system that produces events, regardless of the source being a non-SAP application or 3rd party IoT platform. 

### Flow (Mandatory)

This illustrates event-based integration options for automation of events from different systems to business actions in the SAP ecosystem. In this mission, you will learn how to configure and create an event-driven application by implementing the events-to-actions framework in SAP BTP with events from Microsoft Azure or AWS integrating with business processes in SAP S/4HANA.

The architecture is based on leveraging the services of SAP Business Technology Platform which includes event-based integration with SAP Integration Suite, SAP Event Mesh/SAP Advanced Event Mesh , SAP Build Process Automation , SAP HANA Cloud, SAP Destination Service, SAP Private Link service, SAP Connectivity Service and Cloud Connector and a Node.js extension application on the SAP Cloud Foundry runtime.

The following steps depict the information flow across systems (in both scenarios)
- Event is triggered from source systems like Microsoft Azure/AWS/Telco IOT Platform (in the case of IOT scenario) or any other system and is published on to SAP Integration Suite, SAP Event Mesh/SAP Advanced Event Mesh from the Event-to-Business-Action framework (extension app),
- processor module(part of the Events-to-Business-Action framework) endpoint is subscribed to Event Mesh to receive the event.
- processor module leverages the Decisions capability of SAP Build Process Automation to derive business action (For example, Purchase Order Requisition creation in SAP S/4HANA system) based on certain characteristics of incoming event.
- processor module triggers the defined action in the SAP S/4HANA system using the SAP Destination Service and SAP Private Link Service.
In case SAP S/4HANA is on-premise and private cloud – communication with SAP S/4HANA happens via SAP Connectivity Service and Cloud Connector.

### Characteristics (Mandatory)


- A flexible and generic framework that can be easily extensible for any Line of Business (LoB) scenario /workflow/process and any source system events.
- Event-driven integration architecture with SAP Event Mesh as a central hub, including a bi-directional flow of events (Microsoft Azure to SAP S/4HANA and vice versa). We are also evaluating on leveraging Advanced Event Mesh (to be updated soon).
- Enriched with resilient and high availability architectural patterns. [Enhance core ERP business processes with resilient applications on SAP BTP](https://discovery-center.cloud.sap/missiondetail/3501/3542/?tab=projectboard)
- Network security-focused design with SAP Private Link specifically for RISE with SAP customers. [Secure Connectivity with SAP Private Link service](https://discovery-center.cloud.sap/refArchDetail/ref-arch-AWS-Azure-CAP-PLS)


### Examples in an SAP context (Mandatory)

Companies are driving the digitization of the factory, plants, warehouses, and business networks and creating an ecosystem by linking Information Technology (IT) with Operational Technology (OT). Bridging the gaps between different landscapes and processes with integrated frameworks is key for building a seamless, efficient, bi-directional collaborative ecosystem. For instance, in a supply chain logistics scenario, the movement of inventory (e.g., product, pallet) often indicates the next step in the business process. Thus, the manual effort to capture process steps, update the IT systems and trigger subsequent processes can be minimized by integrating events, enriching them with business context and integrating them into business processes.


### Services and Components (Mandatory)

<!-- dc-ref-arch-services-start -->

- [SAP BTP, Cloud Foundry Runtime](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime?region=all)

- [SAP Build Process Automation](https://discovery-center.cloud.sap/serviceCatalog/sap-build-process-automation?region=all)

- [SAP Integration Suite, advanced event mesh](https://discovery-center.cloud.sap/serviceCatalog/advanced-event-mesh?region=all)

- [SAP Private Link Service](https://discovery-center.cloud.sap/serviceCatalog/private-link-service?service_plan=standard&region=all&commercialModel=btpea)

- [SAP HANA Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-hana-cloud?region=all)

- [SAP Business Application Studio](https://discovery-center.cloud.sap/serviceCatalog/business-application-studio?region=all)

- [SAP Connectivity Service](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all)

- [SAP Cloud Identity Services - Identity Authentication](https://discovery-center.cloud.sap/serviceCatalog/identity-authentication?region=all)

- [SAP Authorization and Trust Management Service](https://discovery-center.cloud.sap/serviceCatalog/authorization-and-trust-management-service?region=all)



<!-- dc-ref-arch-services-end -->

### Resources (Mandatory)

<!-- dc-ref-arch-resources-start -->
- [SAP Samples | GitHub ](https://github.com/SAP-samples/btp-events-to-business-actions-framework)
<!-- dc-ref-arch-resources-end -->

- [“Events-to-Business Actions": An event-driven architecture on SAP BTP to implement Industry 4.0 scenarios with Microsoft Azure Services](https://community.sap.com/t5/technology-blogs-by-sap/part-1-events-to-business-actions-quot-an-event-driven-architecture-on-sap/ba-p/13555219)

- [Events-2-Business Action Framework – Create Plant Maintenance Notification in SAP S/4 HANA](https://community.sap.com/t5/technology-blogs-by-members/events-2-business-action-framework-create-plant-maintenance-notification-in/ba-p/13573476#:~:text=Events%2D2%2DBusiness%20Action%20Framework%20%E2%80%93%20Create%20Plant%20Maintenance%20Notification%20in%20SAP%20S/4%20HANA)

### Related Missions

<!-- dc-ref-arch-related-missions-start -->
- [Build Events-to-Business Actions Apps with SAP BTP and MS Azure/AWS](https://discovery-center.cloud.sap/missiondetail/4172/4422/)

- [Integrate Events from Amazon Monitron with SAP S/4HANA using SAP BTP](https://discovery-center.cloud.sap/missiondetail/4345/4628/)

- [Integrate Amazon Rekognition and SAP EHS for PPE Detection](https://discovery-center.cloud.sap/missiondetail/4352/4635/)
<!-- dc-ref-arch-related-missions-end -->