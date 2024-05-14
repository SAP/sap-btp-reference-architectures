<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-build-process-automation",
        "name": "Integrate and extend SAP and non-SAP solutions with SAP Build Process Automation",
        "shortDescription": "Automate business processes across cloud and on-premise solutions using workflow and robotic process automation capabilities.",
        "archDiagramLink": "images/SAP_Build_Process_Automation.svg",
        "tags": "automation, enterprise automation, workflow, rpa, lcnc, low-code no-code, integration, cloud, on-premise, isa-m",
        "category": "Application Development, Automation"
    }
dc-ref-arch-metadata  -->

<!-- dc-ref-arch-detail-page-start -->
## **Integrate and extend SAP and non-SAP solutions with SAP Build Process Automation**

SAP Build Process Automation is a citizen developer solution to adapt, improve, and innovate business processes with no-code workflow management and robotic process automation capabilities.

SAP Build Process Automation enables business users and technologists to become citizen developers. With intuitive low-code and no-code capabilities, the solution supports you in driving automation by tapping into the expertise of citizen developers.

This reference architecture describes how you can use SAP Build Process Automation to integrate and extend SAP and non-SAP solutions in cloud and hybrid landscapes. It also related to the Robot Process Automation use case pattern of the SAP Integration Solution Advisory Methodology.

### Flow

The SAP Build Process Automation architecture diagram highlights five key flows when creating process automations across systems.

1. End users can access SAP Build Process Automation via the web and mobile native application(s).

    a. SAP Build Work Zone Web (standard / advanced edition)

    b. SAP Build Work Zone Advanced (mobile application for advanced edition)

    c. SAP Mobile Start (only SAP Start & standard edition for now)

2. For identity management and authentication, SAP Build Process Automation relies on SAP Cloud Identity Services - Identity Authentication as the identity provider. SAP Cloud Identity Services serve as central facade for the identity and access management. In this context, SAP Cloud Identity Services - Identity Authentication offers secure authentication or a federation with third party identity providers. The SAP Cloud Identity Services - Identity Directory stores the SAP identities. SAP Cloud Identity Services can also be used as a proxy for a customer owned identity provider.

3. SAP Build Process Automation as a solution consists of multiple components enabling different capabilities out of the box which cannot be decoupled from the product. When SAP Build Process Automation is activated in a subaccount of SAP BTP, these components will be invisible in the list of subscriptions and service instances: They are all an integral part of the solution itself (SAP Build Process Automation subscription). This includes services like Decisions, Process Visibility, Processes and Automations.

4. SAP Build Process Automation integrates via the SAP Connectivity service with other SAP BTP services and with applications outside of SAP BTP. The integration is based on APIs which are provided via different channels as Live API using Graph, SAP Cloud Application Programming Model, ABAP RESTful Application Programming Model OData destinations, SAP systems, API Business Hub Enterprise or via API specifications using SAP Business Accelerator Hub, uploading API specifications and building API actions from scratch.

5. Processes in SAP Build Process Automation can be triggered via events, APIs, schedules and forms. Forms can be provided based on SAP Build Process Automation Forms, UI5 applications or SAP Build Apps.

6. When moving business content from one environment to another – for example from development to test – this can be achieved via manual export/import or via the more elaborated integration with SAP Cloud Transport Management.

### Characteristics

- Central automation solution across hybrid SAP landscapes: SAP Build Process Automation allows to easily build approval processes across systems with SAP Task Center as a centralized access for end users to manage their tasks.

- Support of third-party identity providers: SAP Cloud Identity Services - Authentication allows federation with third party Identity Providers and SAP Cloud Identity Services – Provisioning allows provisioning of user/role assignments from a third-party source.

- Global User ID: Globally unique user identifier defined by SAP Cloud Identity Services-Identity Authentication and used by SAP Build Process Automation.

- Cloud and on-premise solution integration: Apart from integrating with various SAP and third party cloud solutions, SAP Build Process Automation can also be configured to work with SAP ECC, SAP S/4HANA and S/4HANA Cloud, private edition.

- Predefined content for SAP Build Process Automation is directly available via the integrated store and can be used with or without adoption based on customer needs.

### Examples in an SAP context

SAP Build Process Automation is used in various use cases across all Lines of Businesses and all industries:

1. Mass maintenance of a scheduling agreements

    In this use case business experts are enabled to accelerate the automation of creation and change of scheduling agreements in a transparent way and provides feasibility to meet business requirements. The use case includes approval decisions, automation of master data content.

    SAP Build Process Automation allows efficient processing of master data creation or change and helps in process optimization for the master data team including approval of the master data in SAP. By automating this process, organizations can streamline their supply chain operations and improve productivity.

    Based on selection criteria, the process is triggered in SAP Build Process Automation and a scheduling agreement is created or changed (depending on the choice of operation) for all valid scheduling agreements

2. Non-repairable part auto recording with goods movement

    In this use case business experts are enabled to accelerate recording of non-repairable equipment or spare parts and post goods movement of spare part to a non-repairable storage location in a transparent approach and provides feasibility to meet business requirements. It also includes approval decisions.

    Mass recording of non-repairable status and posting goods movement for parts which are not repairable for now but might be repairable later is a regular activity in repair business. The process of declaring parts with high volume is time consuming, manually intensive and error prone as there are multiple manual steps involved to complete process. Due to the high frequency and volume of parts to be declared as non-repairable, this solution will help to expedite the time and effort to perform this task.

    Based on selection criteria, the process is triggered in SAP Build Process Automation and system status is changed for equipment and it is marked as deactivated, or a goods movement is posted for spare part to a non-repairable storage location in SAP S/4HANA system.    

3. Creation and approval of mass job requisition

    This use case streamlines and automates the process of creating and approving job requisition for the open positions with multiple vacancies that are existing in position organization chart within the SAP SuccessFactors Employee Central (EC).

    It does so by extracting the necessary data from a source file with position data, often an excel document, and utilizing relevant APIs to create and approve the requisition. Upon successful completion of the process the job requisition is in the 'Open' status. These requisitions can be published to internal and external job sites, making it available for candidates to view and apply for the respective job positions. This end-to-end process not only reduces manual data entry and processing but also enhances the speed and efficiency of job requisition creation and approval within the organization's hiring workflow.   

4. Create customer material info records

    The business requires a solution to reduce the manual effort by the internal sales representative for creation of customer material info record in SAP S/4HANA system.

    When customer sends a request to create customer material info records (CMIR) to SAP S/4HANA system, automation will validate for duplicate entry and initiate workflow for approval. Once approved, the customer material info records (CMIR) will be automatically created in SAP S/4HANA system via API.

    Organizations receives a request via emails with attachment to create customer material info records (CMIR) into SAP S/4HANA system. There have been issues reported with data inconsistencies in areas like purchasing, procurement and in other similar areas due to inefficiency to address such request. Also, the SAP S/4HANA system is prone to human errors while with data entries and low productivity due to lack of proper automatic mechanism to cater such request.
<!-- dc-ref-arch-detail-page-end -->

### Services and Components

<!-- dc-ref-arch-services-start -->
- [SAP Business Application Studio](https://discovery-center.cloud.sap/serviceCatalog/business-application-studio?region=all)
- [SAP Connectivity Service](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all)
- [Destination](https://discovery-center.cloud.sap/serviceCatalog/destination?region=all)
- [SAP Document Management service, integration option](https://discovery-center.cloud.sap/serviceCatalog/document-management-service-integration-option?region=all)
- [SAP Cloud Identity Services](https://discovery-center.cloud.sap/serviceCatalog/identity-authentication?region=all)
- [SAP Integration Suite](https://discovery-center.cloud.sap/serviceCatalog/integration-suite?region=all)
- [SAP Build Apps](https://discovery-center.cloud.sap/serviceCatalog/sap-build-apps?region=all)
- [SAP Build Process Automation](https://discovery-center.cloud.sap/serviceCatalog/sap-build-process-automation?region=all)
- [SAP Build Work Zone](https://discovery-center.cloud.sap/serviceCatalog/sap-build-work-zone-advanced-edition?region=all)
<!-- dc-ref-arch-services-end -->

### Resources

<!-- dc-ref-arch-resources-start -->
- [SAP Community blog posts](https://community.sap.com/t5/c-khhcw49343/SAP+Build+Process+Automation/pd-p/73554900100800003832)
- [SAP product documentation](https://help.sap.com/viewer/product/PROCESS_AUTOMATION/Cloud)
- [SAP Tutorials](https://developers.sap.com/tutorial-navigator.html?tag=software-product%3Atechnology-platform%2Fsap-build%2Fsap-build-process-automation)
- [SAP Learning Journeys](https://learning.sap.com/learning-journeys?page=1&query=sap+build+process+automation)
<!-- dc-ref-arch-resources-end -->

### Related Missions

<!-- dc-ref-arch-related-missions-start -->
- [Process and approve your invoices with SAP Build Process Automation](https://discovery-center.cloud.sap/index.html#/missiondetail/3260/3344/)
- [Extend SAP S/4HANA with SAP Build Process Automation](https://discovery-center.cloud.sap/index.html#/missiondetail/4163/4406/)
- [Extend Pre-built Automation Procurement Packages in SAP Build Process Automation](https://discovery-center.cloud.sap/index.html#/missiondetail/4018/4222/)
<!-- dc-ref-arch-related-missions-end -->
