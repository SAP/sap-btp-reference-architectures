<!-- [IMPORTANT] Do not remove the comments below. These comments are necessary for importing the content to DC -->

<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-events-businessactions",
        "name": "Events to business framework",
        "shortDescription": "Implement event driven architecture based applications on SAP BTP using SAP CAP, SAP Advanced Event Mesh and SAP Build Process Automation. The architecture offers framework for building Industry 4.0/eventing related applications.",
        "archDiagramLink": "images/Events-to-business-actions-framework_diagram.png",
            "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Events-to-business-actions-framework.drawio"
        }
    ],
        "tags": "event-driven applications, event mesh, advanced event mesh, sap btp, hyperscaler",
        "category": "Hyperscaler, Integration"
    }
dc-ref-arch-metadata  -->

<!-- dc-ref-arch-detail-page-start -->

## Events to business actions framework

As businesses expand, their enterprise IT landscapes become more intricate, and they need to automate and optimize daily tasks with various software applications, systems, and processes. 
Companies are driving the digitization of the factory, plants, warehouses, and business networks and creating an ecosystem by linking Information Technology (IT) with Operational Technology (OT). Bridging the gaps between different landscapes and processes with integrated frameworks is key for building a seamless, efficient, bi-directional collaborative ecosystem. For instance, in a supply chain logistics scenario, the movement of inventory (e.g., product, pallet) often indicates the next step in the business process. Thus, the manual effort to capture process steps, update the IT systems and trigger subsequent processes can be minimized by integrating events, enriching them with business context and integrating them into business processes. On similar lines, events can be produced from systems and applications as well for e.g emails, business events on enterprise applications etc. This brings the need to trigger business processes as a response to these events.

To facilitate communication across these landscapes without overburdening the systems, decoupled/asynchronous communication between application endpoints is an effective solution to improve performance and scalability. One of the ways to achieve this on SAP BTP is to develop and extension applications based on event-driven architecture. 

The events-to-business actions framework is an event-driven side-by-side extension application that integrates any type of event from systems/applications (providers) into the SAP ecosystem (consumer) via SAP BTP. This application helps to configure actions that need to be executed in SAP LoB systems based on the events that are received in SAP Integration Suite, advanced event mesh. The application scenario you will develop in this tutorial leverages the Events-To-Business actions framework (extension application).

### Flow 

This illustrates event-based integration options for automation of events from different systems to business actions in the SAP ecosystem. In this reference architecture, you will learn how to configure and create an event-driven application by implementing the events-to-actions framework in SAP BTP with events from Microsoft Azure or AWS integrating with business processes in SAP S/4HANA. This architecture specifically focused on Industry 4.0 scenario, hence Microsoft Azure and AWS's IOT services are leveraged.

The architecture is based on leveraging the services of SAP BTP which includes event-based integration with SAP Integration Suite, SAP Event Mesh/SAP Advanced Event Mesh , SAP Build Process Automation , SAP HANA Cloud, SAP Destination Service, SAP Connectivity service with cloud connector and a Node.js extension application on the SAP Cloud Foundry runtime. An alternative architecture can be considered with SAP Private Link service for integrating SAP BTP and SAP S/4HANA in scenarios where both SAP BTP and SAP S/4HANA run on the same hyperscaler environment (Microsoft Azure or AWS).

The following steps depict the information flow across systems (in both scenarios)

1. Application admin logs into SAP BTP extension application based on Events to Business Actions Framework via SAP Build Workzone to configure the business rules/decisions and the business actions that needs to be triggered in the business systems. 

2. Event is triggered from source systems like Microsoft Azure/AWS/Telco IOT Platform (in the case of IOT scenario) or any other system. 

3. These events are published on to SAP Integration Suite, SAP Event Mesh/SAP Advanced Event Mesh. As the processor module's(part of the Events-to-Business-Action framework) endpoint is subscribes to Event Mesh, the event is received.

4. Processor module(part of the Events-to-Business-Action framework) leverages the Decisions capability of SAP Build Process Automation to derive business action (For example, Purchase Order Requisition creation in SAP S/4HANA system) based on certain characteristics of incoming event.

5. The defined action is triggered in the SAP S/4HANA system using the SAP Destination Service and SAP Connectivity service leveraging cloud connector setup.
In case SAP S/4HANA and SAP BTP are on same hyperscaler, communication with SAP S/4HANA happens via SAP Private Link Service.

### Characteristics 


- A flexible and generic framework that can be easily extensible for any Line of Business (LoB) scenario /workflow/process and any source system events.
- Event-driven integration architecture with SAP Integration Suite, advanced event mesh as a central hub, including a bi-directional flow of events (Microsoft Azure to SAP S/4HANA).
- Enriched with resilient and high availability architectural patterns. [Enhance core ERP business processes with resilient applications on SAP BTP](https://discovery-center.cloud.sap/missiondetail/3501/3542/?tab=projectboard)
- Network security-focused design with SAP Private Link service specifically for RISE with SAP customers. [Secure Connectivity with SAP Private Link service](https://discovery-center.cloud.sap/refArchDetail/ref-arch-AWS-Azure-CAP-PLS)


### Examples in an SAP context

Companies are driving the digitization of the factory, plants, warehouses, and business networks and creating an ecosystem by linking Information Technology (IT) with Operational Technology (OT). Bridging the gaps between different landscapes and processes with integrated frameworks is key for building a seamless, efficient, bi-directional collaborative ecosystem. For instance, in a supply chain logistics scenario, the movement of inventory (e.g., product, pallet) often indicates the next step in the business process. Thus, the manual effort to capture process steps, update the IT systems and trigger subsequent processes can be minimized by integrating events, enriching them with business context and integrating them into business processes.

<!-- dc-ref-arch-detail-page-end -->

### Services and Components

<!-- dc-ref-arch-services-start -->

- [SAP BTP, Cloud Foundry Runtime](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->

- [SAP Build Process Automation](https://discovery-center.cloud.sap/serviceCatalog/sap-build-process-automation?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->

- [SAP Integration Suite, advanced event mesh](https://discovery-center.cloud.sap/serviceCatalog/advanced-event-mesh?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->

- [SAP Private Link service](https://discovery-center.cloud.sap/serviceCatalog/private-link-service?service_plan=standard&region=all&commercialModel=btpea)

- [SAP HANA Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-hana-cloud?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->

- [SAP Business Application Studio](https://discovery-center.cloud.sap/serviceCatalog/business-application-studio?region=all)

- [SAP Connectivity Ssrvice](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->

- [SAP Authorization and Trust Management service](https://discovery-center.cloud.sap/serviceCatalog/authorization-and-trust-management-service?region=all) 

<!-- dc-ref-arch-services-end -->

### Resources

<!-- dc-ref-arch-resources-start -->

- [SAP Samples | GitHub ](https://github.com/SAP-samples/btp-events-to-business-actions-framework)


- [“Events-to-Business Actions": An event-driven architecture on SAP BTP to implement Industry 4.0 scenarios with Microsoft Azure Services](https://community.sap.com/t5/technology-blogs-by-sap/part-1-events-to-business-actions-quot-an-event-driven-architecture-on-sap/ba-p/13555219)

- [Events-2-Business Action Framework – Create Plant Maintenance Notification in SAP S/4 HANA](https://community.sap.com/t5/technology-blogs-by-members/events-2-business-action-framework-create-plant-maintenance-notification-in/ba-p/13573476#:~:text=Events%2D2%2DBusiness%20Action%20Framework%20%E2%80%93%20Create%20Plant%20Maintenance%20Notification%20in%20SAP%20S/4%20HANA)

<!-- dc-ref-arch-resources-end -->

### Related Missions

<!-- dc-ref-arch-related-missions-start -->

- [Build Events-to-Business Actions Apps with SAP BTP and MS Azure/AWS](https://discovery-center.cloud.sap/missiondetail/4172/4422/)

- [Integrate Events from Amazon Monitron with SAP S/4HANA using SAP BTP](https://discovery-center.cloud.sap/missiondetail/4345/4628/)

- [Integrate Amazon Rekognition and SAP EHS for PPE Detection](https://discovery-center.cloud.sap/missiondetail/4352/4635/)

<!-- dc-ref-arch-related-missions-end -->
