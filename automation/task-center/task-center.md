<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-sap-task-center",
        "name": "Establish a central inbox with SAP Task Center",
        "shortDescription": "SAP Task Center helps you integrate tasks into a central solution.",
        "archDiagramLink": "images/Establish-a-central-inbox-with-SAP-Task-Center_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Establish-a-central-inbox-with-SAP-Task-Center.drawio"
        }
    ],

        "tags": "SAP Task Center, integration, task providers, one workflow inbox, task federation, ISA-M",
        "category": "Automation,Integration"
    }
dc-ref-arch-metadata  -->
<!-- dc-ref-arch-detail-page-start -->
## **Establish a central inbox with SAP Task Center**

SAP Task Center enables integration with SAP applications to provide a single entry point for end users to access all their assigned tasks. The tasks can be accessed by end users through the SAP Task Center UI clients.

You can use SAP Task Center as a unified inbox for tasks across multiple applications with integrated user experience. Tasks from multiple SAP solutions are gathered in one list and are ready to be processed in just one click, shortening the completion time for business-critical tasks. For example, business users can process all their tasks from the connected systems, without the need to switch and log in separately into different inboxes.

This reference architecture also refers to the Process Automation cross use case pattern of the SAP Integration Solution Advisory Methodology.

### Flow

The reference architecture diagram shows the SAP Task Center integration with various task providers.

1. For identity management and authentication, the SAP Task Center tenant relies on SAP Cloud Identity Services-Identity Authentication as the identity provider (IdP). SAP Cloud Identity Services serve as central fascade for the identity & access management. The SAP Cloud Identity Services - Identity Directory (IdDS) stores the SAP identities and the SAP Cloud Identity Services - Authentication (IAS) allow a secure authentication or a federation with third-party Identity Providers.

2. Each task provider, which is about to be integrated with SAP Task Center, must be able also to work with Identity Authentication as a hard prerequisite. To integrate а task provider with SAP Task Center, the following general guidelines should be followed:

    a) The users, who would consume SAP Task Center, must be available in both SAP Cloud Identity Services and the task provider system.

    b) The user identities must include the Global User ID, so that a user can be correlated across the different systems. For more information, see [Global User ID in Integration Scenarios](https://help.sap.com/docs/cloud-identity/system-integration-guide/global-user-id-in-integration-scenarios).

    c) The user entries must include essential user data, such as an email address and a display name.
   
    d) Sign-on should be configured between the task provider and Identity Authentication to enable navigation between SAP Task Center and the task provider.
   
    e) Tasks must be correlated with Global User ID, when provided to SAP Task Center. For example, the list of recipient users of a task must contain Global User IDs.

3. SAP Task Center communicates with the task provider applications via predefined destinations in a customer subaccount. For more information, see [Destinations](https://help.sap.com/docs/task-center/sap-task-center/destinations).

4. To integrate with SAP S/4HANA systems and receive on-premise tasks in SAP Task Center, a SAP Cloud Connector must be set up as part of the destination configuration.

5. End users can access SAP Task Center via various application clients:

    a. SAP Task Center Web app

    b. To-Dos in SAP Mobile Start

    c. To-Dos in SAP Start
   
   For more information, see [Using SAP Task Center](https://help.sap.com/docs/task-center/sap-task-center/using-sap-task-center).

### Characteristics

An architecture for SAP Task Center integration can be characterized as follows:

- **Single entry point for accessing tasks**: SAP Task Center allows end users to access all their assigned tasks from one inbox.

- **Global User ID**: Globally unique user identifier defined by SAP Cloud Identity Services and used by SAP Task Center and all task providers.

- **Support of third-party identity providers**: SAP Cloud Identity Services - Authentication (IAS) allows a federation with third-party Identity Providers (for SAP Task Center using the user store should be enabled)

- **SAP on-premise solutions integration**: Apart from integrating with various SAP cloud solutions, SAP Task Center can be configured to work with SAP S/4HANA and SAP S/4HANA Cloud, private edition.

- **Different application clients**: Tasks federated by SAP Task Center can be accessed from the SAP Task Center Web app, To-Dos in SAP Mobile Start and the To-Dos in SAP Start.

### Examples in an SAP Context

SAP offers various SAP cloud and on premise solutions, which offer separate inbox experiences. With SAP Task Center the following is achieved:

- Reduce the time spent by users navigating through various systems and finding items that require their approval or attention.

- Improve the approval or completion time for critical items (which impact business operations if not approved on time).

- Improve the quality and consistency of approvals.
<!-- dc-ref-arch-detail-page-end -->

### Services and Components
<!-- dc-ref-arch-services-start -->
- [SAP Build Work Zone](https://discovery-center.cloud.sap/serviceCatalog/sap-build-work-zone-advanced-edition?region=all)
- [SAP Task Center](https://discovery-center.cloud.sap/serviceCatalog/sap-task-center?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->
- [SAP Cloud Identity Authentication](https://discovery-center.cloud.sap/serviceCatalog/identity-authentication?region=all)
- [SAP Cloud Identity Provisioning](https://discovery-center.cloud.sap/serviceCatalog/identity-provisioning?region=all)
- [SAP Connectivity service](https://discovery-center.cloud.sap/serviceCatalog/connectivity-service?region=all)
- [SAP Destination service](https://discovery-center.cloud.sap/serviceCatalog/destination?region=all)
<!-- dc-ref-arch-services-end -->

### Resources
<!-- dc-ref-arch-resources-start -->
- [SAP Task Center (SAP Help Portal)](https://help.sap.com/docs/task-center)
- [SAP Task Center (Guided Answers)](https://ga.support.sap.com/dtp/viewer/index.html#/tree/3109/actions/47627)
- [SAP Task Center (SAP Community Topic Page)](https://pages.community.sap.com/topics/task-center)

<!-- dc-ref-arch-resources-end -->

### Related Missions
<!-- dc-ref-arch-related-missions-start -->
- [Establish a Central Inbox with SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3774/3813/)
- [Integrate Your SAP S/4HANA Cloud Tasks Into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3906/4071/)
- [Integrate Your SAP S/4HANA Tasks Into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3910/4076/)
- [Integrate Your SAP SuccessFactors Tasks Into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3816/3869/)
- [Integrate Your SAP Concur Tasks Into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3883/3962/)
- [Integrate Your SAP Cloud for Customer into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/4235/4489/)
- [Integrate Your SAP Fieldglass Tasks Into SAP Task Center](https://discovery-center.cloud.sap/missiondetail/3911/4077/)
<!-- dc-ref-arch-related-missions-end -->
