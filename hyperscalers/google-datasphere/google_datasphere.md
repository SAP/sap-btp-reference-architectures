<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-google-datasphere",
        "name": "Explore your hyperscaler data with SAP Datasphere Integration",
        "shortDescription": "Combine the data processing and analytical capabilities of the SAP Business Technology Platform based on SAP Datasphere and SAP Analytics Cloud with database, storage and AI capabilities of Google Cloud.",
        "archDiagramLink": "images/Explore-your-Hyperscaler-data-with-SAP-Datasphere_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Explore-your-Hyperscaler-data-with-SAP-Datasphere.drawio"
        }
    ],

        "tags": "Hyperscaler, google, google cloud platform, gcp, sap datasphere, google bigquery, google cloud storage, vertex ai",
        "category": "Hyperscaler, Integration, Data Analytics"
    }
dc-ref-arch-metadata  -->
<!-- dc-ref-arch-detail-page-start -->
## **Explore your hyperscaler data with SAP Datasphere**

Combine business critical data from SAP business applications with data services from hyperscaler providers such as AWS, Microsoft Azure, and Google Cloud using the data federation and analytical capabilities of SAP Datasphere.  

SAP Datasphere enables a business data fabric architecture that uniquely harmonizes mission-critical data across the organization, unleashing business experts to make the most impactful decisions. It provides federated data access and remote table replication from SAP line of business solutions. In this architecture, non-SAP data from hyperscaler services are combined with SAP data in SAP Datasphere data models to help derive better business insights, faster. 

**A.    Federate data from hyperscaler data sources**

Google BigQuery, Azure Data Lake, Amazon Redshift and Databricks delta lake are examples of some hyperscaler and 3rd party analytical data stores that are used for different kinds of external data, especially for IoT, analytics, trends and Ads data. They are also good choices for importing public datasets or analytical datasets from 3rd party line of business applications like Salesforce, Workday, etc. By federating the data from these data stores into SAP Datasphere, the built-in analytical in-memory capabilities of SAP HANA Cloud can be used to analyze the combined dataset, while avoiding lengthy data transfer and costly ETL processing. In the best case, the data is federated from all sources and the resulting analytical dashboard is displayed real-time in SAP Analytics Cloud. 

**B.    Replicating SAP business data to cloud storages with SAP Datasphere Replication Flow**

SAP Datasphere now allows near real-time replication of SAP business data out to the cloud storages or to targets such as Confluent Kafka directly without the need to persist data in between, through its replication flow feature. Replication flows also support replicating delta loads automatically and supports features such as automatic recovery without the need for any manual intervention.   

**C.    Importing data into SAP Datasphere from cloud storages with Data Flow**

SAP Datasphere’s Data Flow integration feature can be used to import datasets from a cost-efficient object store like Google Cloud Storage or Amazon S3. With this approach the data can be transformed during the transfer and persisted "physically" in SAP Datasphere.  

<!-- dc-ref-arch-detail-page-end -->

### BTP services / SAP solutions
<!-- dc-ref-arch-services-start -->
The reference architecture for Hypescaler & SAP Datasphere Integration uses the following SAP BTP services:

- [SAP Datasphere](https://discovery-center.cloud.sap/serviceCatalog/sap-datasphere?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->: SAP Datasphere enables a business data fabric architecture that uniquely harmonizes mission-critical data across the organization, unleashing business experts to make the most impactful decisions. It combines previously discrete capabilities into a unified service for data integration, cataloging, semantic modeling, data warehousing, and virtualizing workloads across SAP and non-SAP data.

- [SAP Analytics Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-analytics-cloud?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->: SAP Analytics Cloud is an open cloud solution built for software as a service (SaaS) that combines analytics and planning to instantly move from insight to action. Decision makers can simulate any scenario and automatically generate plans from smart predictions. SAP Analytics Cloud utilizes the full context of SAP data and brings analytics closer to the point of decision, while comprehensive prebuilt SAP business content is available to accelerate analytics and planning projects.
<!-- dc-ref-arch-services-end -->

### Resources
<!-- dc-ref-arch-resources-start -->
For more information about the different technologies used in the reference architecture above, more detailed explanations and example code, check out the following resources:
- SAP Help Portal:
    - [SAP Datasphere](https://help.sap.com/docs/SAP_DATASPHERE)
    - [SAP Analytics Cloud](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD)

- SAP Community blog posts:
    - [SAP Datasphere – the next generation of SAP Data Warehouse Cloud](https://blogs.sap.com/2023/10/11/sap-datasphere-the-next-generation-of-sap-data-warehouse-cloud/)
    - [Powering Efficient Supply Chains: SAP Datasphere’s Integration with Google Cloud’s Architecture](https://blogs.sap.com/2023/06/29/powering-efficient-supply-chains-sap-dataspheres-integration-with-google-clouds-architecture/)
    - [SAP Datasphere and Google Cloud Platform Integration – A Success Story at Brightspeed](https://community.sap.com/t5/technology-blogs-by-sap/sap-datasphere-and-google-cloud-platform-integration-a-success-story-at/ba-p/13582891)
    - [SAP and Google Cloud Data Harmonization for Efficient Analytics & Reporting — Veolia](https://community.sap.com/t5/technology-blogs-by-sap/sap-and-google-cloud-data-harmonization-for-efficient-analytics-amp/ba-p/13605578)
    - [Replication Flows - SAP Datasphere and Google BigQuery](https://community.sap.com/t5/technology-blogs-by-sap/replication-flows-sap-datasphere-and-google-big-query/ba-p/13581256)
    - [Drive business innovation using SAP and Google Cloud Data Platforms](https://community.sap.com/t5/technology-blogs-by-sap/drive-business-innovation-using-sap-and-google-cloud-data-platforms/ba-p/13573574)
    - [Federated Analytics with SAP Datasphere : A DECATHLON Story](https://community.sap.com/t5/technology-blogs-by-sap/federated-analytics-with-sap-datasphere-a-decathlon-story/ba-p/13527965)

<!-- dc-ref-arch-resources-end -->

### Related SAP Discovery Center Missions
<!-- dc-ref-arch-related-missions-start -->
If you would like to implement solutions that are related to this reference architecture and the technologies used you may continue with the following SAP Discovery Center missions:
- [Integrate Google BigQuery and SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3409/3449/)
- [Enable Category Management with BigQuery and SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3666/3709/)
- [Integrating Google BigQuery with SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3409/3449/)
- [Integrating Azure Data Explorere with SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3433/3473/)
- [Integrate Amazon Athena with SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3401/3441/)
- [Federating data from Databricks delta lake into SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/4259/4517/)
- [Data federation from Amazon Redshift using SAP Datasphere](https://discovery-center.cloud.sap/missiondetail/3406/3446/)

<!-- dc-ref-arch-related-missions-end -->
