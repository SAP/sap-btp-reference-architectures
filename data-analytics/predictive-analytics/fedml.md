<!-- dc-ref-arch-metadata : 
    {
        "id": "ref-arch-fedml",
        "name": "Federated Machine Learning",
        "shortDescription": "The SAP Federated ML Python libraries (FedML) applies the Data Federation architecture of SAP Datasphere for intelligently sourcing SAP as well as non-SAP data for Machine Learning experiments done at the Hyperscalers thereby removing the need for replicating or moving data.",
        "archDiagramLink": "images/Federated-Machine-Learning_diagram.png",
    "archDownloadResources" : [
        {
            "type": "drawio",
            "link": "architectures/Federated-Machine-Learning.drawio"
        }
    ],

        "tags": "Data Analytics, Cross, Cloud, SAP Data and Analytics Advisory Methodology, DAAM",
        "category": "Data Analytics, Hyperscaler",
        "labels": "Data Analytics, Artifical Intelligence, Hyperscaler"
    }
dc-ref-arch-metadata  -->

<!-- dc-ref-arch-detail-page-start -->

## **Federated Machine Learning**

This reference architecture relates to the use case pattern "Federated Machine Learning" of the use case category "Predictive Analytics" as defined by the **SAP Data and Analytics Advisory Methodology**.

### Description

The SAP Federated ML Python libraries (FedML) applies the Data Federation architecture of SAP Datasphere for intelligently sourcing SAP as well as non-SAP data for Machine Learning experiments done at any Machine Learning platform thereby removing the need for replicating or moving data. By abstracting the data connection and data load , the FedML library provides end to end platform agnostic integration support for instant data access & discovery of semantically rich business data with just few lines of code.

Traditionally, using a dataset with a machine-learning platform or AI service like Google Vertex AI , Microsoft Azure ML , Amazon Sagemaker or IBM Watsonx.ai requires persisting the data on the ML platform, e.g. in Google Cloud Storage or Databricks delta lake. Using the open-sourced SAP FedML library data accessible in SAP Datasphere (virtually or physically) can be directly used in a Jupyter Notebook to train a ML model or for inference in the ML platform environment.

FedML also supports training ML models in GPU environments through its support for NVIDIA RAPIDS(TM) framework and CUDA libraries. Models trained in ML Platforms can also be deployed in SAP AI Core seamlessly with a few lines of code.

<!-- dc-ref-arch-detail-page-end -->

### BTP services / SAP solutions
<!-- dc-ref-arch-services-start -->
[SAP Datasphere](https://discovery-center.cloud.sap/#/serviceCatalog/sap-datasphere?region=all) <!-- dc-svc-metadata: {"isPrimary": "true"} dc-svc-metadata -->
<!-- dc-ref-arch-services-end -->
### References
<!-- dc-ref-arch-resources-start -->
[SAP Samples (GitHub)](https://github.com/SAP-samples/data-warehouse-cloud-fedml)
<!-- dc-ref-arch-resources-end -->
<!-- dc-ref-arch-related-missions-start -->
### Related SAP Discovery Center Missions
If you would like to implement solutions that are related to this reference architecture and the technologies used you may continue with the following SAP Discovery Center missions:
- [Predict and Analyze Retail Inventory Allocation using FedML](https://discovery-center.cloud.sap/missiondetail/3944/4145/)
- [Predict your Supply Chain with Google Vertex AI and FedML](https://discovery-center.cloud.sap/missiondetail/4200/4453/)
- [Predict Inventory Allocation with Amazon Sagemaker and FedML](https://discovery-center.cloud.sap/missiondetail/4106/4331/)
- [Integrating SAP Datasphere & SAP AI Core with IBM Watsonx using FedML](https://discovery-center.cloud.sap/missiondetail/4449/4735/)
- [Enable External Forecasting on SAP IBP with Google Vertex AI](https://discovery-center.cloud.sap/missiondetail/4249/4506/)
<!-- dc-ref-arch-related-missions-end -->
