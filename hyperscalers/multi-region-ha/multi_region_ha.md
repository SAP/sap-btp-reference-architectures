<!-- [IMPORTANT] Do not remove the comments below. These comments are necessary for importing the content to DC -->

<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-multi-region-ha",
        "name": "Architecting Multi-Region Resiliency for SAP BTP Services",
        "shortDescription": "Ensure business-critical SAP BTP services and applications remain highly available, providing robust disaster recovery and minimal downtime.",
        "archDiagramLink": "ref-arch-multi-region-ha.png",
        "tags": "high availability, muti-region ha, integration suite, cloud integration, workzone, standard edition",
        "category": "Hyperscaler"
    }
dc-ref-arch-metadata  -->

<!-- dc-ref-arch-detail-page-start -->
## Architecting Multi-Region Resiliency for SAP BTP Use Cases
As the adoption of SAP BTP services grows and they become integral to essential business operations, customers are progressing through the platform maturity spectrum, incorporating SAP BTP services into their vital business scenarios. It is acknowledged that SAP BTP services come with built-in multi-AZ resiliency features.

Nevertheless, to enhance the robustness of their solutions, many customers have expressed interest in a multi-region setup of SAP BTP services and use cases. This approach involves geographic redundancy and the use of a load balancer to ensure that, should one region face downtime, the load balancer promptly identifies the problem and reroutes requests to a functioning region, thus maintaining uninterrupted business continuity.

### Flow

The reference architecture diagram shows the Muti-Region High Availability architecture for SAP BTP Services and for the applications built on SAP BTP.

1.  SAP Cloud Integration, SAP Build Workzone Standard Edition, SAP HANA Cloud, and other SAP BTP Services achieve high availability (HA) by utilizing the multi-AZ (multiple Availability Zones) within a single region, satisfying the requirements of most customers. However, for unique situations where customers need these SAP BTP services to switch to another geographical region for disaster recovery (DR) or to adhere to specific compliance/regulatory mandates, a cross-region high availability and disaster recovery configuration is crucial for ensuring sufficient protection. This is also relevant for custom applications (CAP) developed on SAP BTP, guaranteeing their resilience and adherence to compliance standards.

2.  To establish a multi-region architecture for SAP BTP services, it is necessary to set up two SAP BTP subaccounts, for example, one in the US and another in the EU, across different regions. In the event of unavailability in one subaccount or a specific service within it, the other subaccount will take over the service requests. SAP Cloud Integration is configured within these two subaccounts to facilitate this process.

3.  Azure Traffic Manager monitors the health of endpoints in multiple regions (two subaccounts) and uses DNS-based load balancing to route traffic to the healthiest available endpoint. It dynamically updates DNS records to ensure that user requests are directed to the most appropriate and responsive endpoint based on the configured traffic-routing method.

4.  Since each SAP BTP service has its own distinct URL, setting up the SAP Custom Domain service is required to unify access under a single, custom-branded URL. This consolidation simplifies interactions for end-users, system-to-system integrations, and various scenarios, thereby enhancing operational efficiency and the user experience. Even if Azure Traffic Manager routes DNS traffic to a different region, the end user's custom domain URL will remain consistent.

5. To overcome a few constraints such as with SAP HANA SDI's one-way data replication between regions and SAP AEM's manual status change (Active/Standby), as well as other necessary adjustments for implementing a multi-region setup, an open-source application has been developed on SAP BTP. This application automates the process of switching between regions, offering flexibility for both manual and automated scenarios. By addressing these challenges, it ensures uninterrupted data replication and operational continuity in a multi-region environment. The need for the Multi-Region Manager is documented in the Git repository for the stateful scenario.

6.  SAP CI/CD or the Project Piper can be used manage the creation and deployment of numerous iFlows or  Workzone Standard Edition content or the custom applications built on SAP BTP or any other artifacts, ensuring seamless synchronization and consistency across the two subaccounts in the multi-region setup.

7. To ensure high availability in a multi-region setup for scheduled jobs that regularly call SAP BTP services or custom services built on SAP BTP, it is recommended to use an external scheduler with multi-region HA capabilities like Azure Scheduler. This can call the custom domain URL in the background, ensuring consistent and reliable access.

### Characteristics

Characteristics of a Multi-Region includes:

-   **Disaster Recovery Strategy**: Allows customers to tailor custom disaster recovery strategies based on specific business requirements and compliance standards, ensuring resilience and regulatory compliance across different regions.

-   **Scalable Workload Distribution**: Provides the flexibility for customers to scale workload distribution across regions dynamically, adapting to changing business demands and optimizing resource utilization for cost-efficiency.

-   **Unified Access Management**: Offers centralized access management through SAP Custom Domain service, simplifying user authentication and authorization processes across multi-region deployments, enhancing security and operational efficiency.

-   **Tailored Operational Control**: Provides customers with tailored operational control through an open-sourced Multi-Region Manager service on SAP BTP, enabling both manual and automated scenarios for region switching and ensuring uninterrupted data replication and operational continuity.

**Note**: Our evaluation offers an architectural viewpoint on Disaster Recovery strategies that incorporate certain SAP BTP services, alongside hyperscaler services like Azure Traffic Manager. This constitutes one of the potential methodologies for overseeing stateful failovers. It's important to note that this evaluation, the proposed architecture, and the Proof of Concept (PoC) are not part of a standard support package or a production-grade solution. Additionally, they do not cover the assessment of specific customer needs or bespoke use cases.

### Examples in an SAP context

-   **Stateless Scenario** In a stateless scenario for Cloud Integration and SAP Build Workzone Standard Edition, services remain available during a disaster or regional unavailability without the need for data replication between regions. You can learn more about this scenario by following the tutorials in the Git repository.

-   **Stateful Scenario** In a stateful scenario, data is needed to be replicated between regions as services require data to be stored in the database for future processing. Detailed information about this scenario, including Cloud Integration flows using HANA DB for state replication, can be found in the Git repository.

-   **Event Replication Scenario** SAP Advanced Event mesh can be used to setup the DR bridge to replicate the events across the regions. You can find more about this scenario in the git repo for the Cloud Integration flows that uses AEM for state replication.


<!-- dc-ref-arch-detail-page-end -->

### Services and Components
<!-- dc-ref-arch-services-start -->
- [SAP Integration Suite](https://discovery-center.cloud.sap/serviceCatalog/integration-suite) (Optional)
- [Custom Domain Service](https://discovery-center.cloud.sap/serviceCatalog/custom-domain)
- [SAP Build Work Zone, standard edition](https://discovery-center.cloud.sap/serviceCatalog/sap-build-work-zone-standard-edition) (Optional)
- [SAP HANA Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-hana-cloud?region) (Optional)
- [SAP Integration Suite, advanced event mesh](https://discovery-center.cloud.sap/serviceCatalog/integration-https://discovery-center.cloud.sap/serviceCatalog/advanced-event-mesh) (Optional)
- [SAP BTP, Cloud Foundry Runtime](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime) (Optional)
<!-- dc-ref-arch-services-end -->

### Resources


<!-- dc-ref-arch-resources-start -->
- [SAP Samples | GitHub ](https://github.com/SAP-samples/btp-services-intelligent-routing)
<!-- dc-ref-arch-resources-end -->

### Related Missions 


<!-- dc-ref-arch-related-missions-start -->
- [Route Multi-Region Traffic to SAP BTP Services Intelligently](https://discovery-center.cloud.sap/missiondetail/3603/3646/)
<!-- dc-ref-arch-related-missions-end -->
