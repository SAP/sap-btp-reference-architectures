<!-- dc-ref-arch-metadata :
    {
        "id": "ref-arch-open-ai",
        "name": "Retrieval Augmented Generation with GenAI on SAP BTP",
        "shortDescription": "Implement Retrieval-Augmented Generation (RAG) use cases on SAP BTP using SAP Cloud Application Programming (CAP) model. The architecture offers best practices for building multi-tenant applications and vector encoding using CAP and SAP HANA Cloud.",
        "archDiagramLink": "images/multitenant-target.png",
        "tags": "Hyperscaler",
        "category": "Hyperscaler"
    }
dc-ref-arch-metadata  -->
<!-- dc-ref-arch-detail-page-start -->

## **CAP-based multitenant SaaS architecture using Retrieval Augmented Generation (RAG)**

RAG, which stands for "Retrieval-Augmented Generation", is a neural architecture that combines the strengths of large pre-trained language models with external retrieval or search mechanisms. The main goal of the RAG architecture is to improve the capability of language models by allowing them to pull relevant information from a vast corpus, much like how search engines retrieve relevant web pages based on queries. RAG is used for various tasks such as question answering and knowledge-intensive NLP tasks. The architecture represents an interesting fusion of retrieval-based and generation-based approaches to NLP.

In this reference architecture pattern, how to seamlessly combine various Large Language Models (LLMs) using SAP AI Core. Maximize the potential of LangChain in [CAP](https://cap.cloud.sap/docs/) model and implement advanced methods such as custom schema-based output parsing or Retrieval Augmented Generation (RAG) with embeddings and a vector database to further enhance the benefits for your specific needs. This reference architecture accommodates both Cloud Foundry and Kyma runtimes, providing adaptability in your endeavor to leverage GenAI on SAP BTP.

### Flow

Here is a high-level flow of how RAG architecture works:

**Question Encoding**: The user provides a question or prompt, which is then encoded by a sequence-to-sequence model into a dense vector.

**Document Retrieval**: This dense vector is used as a query to retrieve relevant documents (or passages) from a large corpus. The retrieval is typically done using a dense vector space search, where documents in the corpus are pre-embedded in the same dense vector space. The top-k most relevant documents or passages are retrieved based on their proximity to the query vector.

**Answer Generation**: The retrieved documents and the original question are fed into a Large Language Model to generate an answer. The model is fine-tuned on a downstream task to generate relevant responses based on both the input question and the retrieved passages.

### Characteristics

Key characteristics of RAG architecture includes:

**Increased Knowledge**: Even if the base LLM has not been trained on certain information, as long as that information exists in the corpus used for retrieval, RAG can still provide relevant answers.

**Flexibility**: By changing the underlying corpus, RAG can be adapted to different domains or knowledge bases.

**Memory Efficiency**: Instead of having to increase the size of the language model to store more information, RAG leverages external data sources, keeping the model size manageable.

### Examples in an SAP Context

The reference architecture illustrates a multitenant application developed by a potential SAP partner or customer, tailored for SAP Business Technology Platform (SAP BTP). This scenario presents a SaaS solution for enhancing customer support within a travel agency, utilizing advanced email insights and automation. The system analyzes incoming emails using Large Language Models (LLMs) to offer core insights such as categorization, sentiment analysis and urgency assessment. It goes beyond basic analysis by extracting key facts and customizable fields like location, managed through a dedicated configuration page.

One innovative feature involves utilizing email embeddings to identify similar historical emails, aiding in understanding how similar requests were handled previously. This fosters consistent and efficient customer service. The code also demonstrates the capabilities of summarizing and translating both email subject and body, enabling streamlined comprehension across languages.

Furthermore, the system takes automation to the next level by generating potential responses for customer inquiries. This response generation is influenced by configurable actions and services, enhancing response accuracy and speed. The flexibility to connect with SAP systems like SAP Concur adds an enterprise dimension, allowing seamless integration of processes and data.

<!-- dc-ref-arch-detail-page-end -->

### BTP services / SAP solutions

<!-- dc-ref-arch-services-start -->

The reference architecture for CAP-based multitenant SaaS architecture using Retrieval Augmented Generation (RAG) uses the following SAP BTP services:

- [SAP Business Application Studio](https://discovery-center.cloud.sap/serviceCatalog/business-application-studio?region=all): SAP Business Application Studio (the next generation of SAP Web IDE) is a powerful and modern development environment, tailored for efficient development of business applications for the Intelligent Enterprise. Available as a cloud service, it provides developers a desktop-like experience similar to market leading IDEs, while accelerating time-to-market with high-productivity development tools such as wizards and templates, graphical editors, quick deployment, and more.

- [SAP Continuous Integration and Delivery](https://discovery-center.cloud.sap/serviceCatalog/continuous-integration--delivery?region=all): SAP Continuous Integration and Delivery lets you configure and run predefined continuous integration and delivery (CI/CD) pipelines that automatically build, test, and deploy your code changes to speed up your development and delivery cycles.

- [SAP Cloud Transport Management](https://discovery-center.cloud.sap/serviceCatalog/cloud-transport-management?region=all): SAP Cloud Transport Management service lets you manage software deliverables between accounts of different environments (such as Cloud Foundry, ABAP, and Neo), by transporting them across various runtimes. This includes application artifacts as well as their respective application-specific content.

- [SAP HANA Cloud](https://discovery-center.cloud.sap/serviceCatalog/sap-hana-cloud?region=all): SAP HANA Cloud is a database-as-a-service that powers mission-critical applications and real-time analytics with one solution at petabyte scale. Converge relational, graph, spatial, and document store and develop smart applications with embedded machine learning. Process mission-critical data at proven in-memory speed and manage it more efficiently with integrated multi-tier storage.

- [SAP AI Core](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-core?region=all): SAP AI Core is a service in the SAP Business Technology Platform that is designed to handle the execution and operations of your AI assets in a standardized, scalable, and hyperscaler-agnostic way. It provides seamless integration with your SAP solutions. Any AI function can be easily realized using open-source frameworks. SAP AI Core supports full lifecycle management of AI scenarios.

- [SAP AI Launchpad](https://discovery-center.cloud.sap/serviceCatalog/sap-ai-launchpad?region=all): SAP AI Launchpad is a multitenant software as a service (SaaS) application in SAP Business Technology Platform. Customers and partners can use SAP AI Launchpad to manage AI use cases (scenarios) across multiple instances of AI runtimes (such as SAP AI Core).

- [PostgreSQL on SAP BTP, hyperscaler option](https://discovery-center.cloud.sap/serviceCatalog/postgresql-hyperscaler-option?region=all): PostgreSQL on SAP BTP, hyperscaler option provides a managed relational database service, based on native PostgreSQL offerings from cloud providers AWS, Microsoft Azure, Google Cloud Platform and Alicloud.

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

- Documentation: [Azure OpenAI Service](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
- Blog post: [SAP BTP Use Cases Kick-Start Transformation with Pre-Built Business Content](https://news.sap.com/2023/05/sap-btp-use-cases-art-of-the-possible/)
- GitHub: [Develop a CAP-based (multitenant) application using GenAI and RAG on SAP BTP](https://github.com/SAP-samples/btp-cap-genai-rag)

<!-- dc-ref-arch-resources-end -->

### Related Missions and Tutorials

<!-- dc-ref-arch-related-missions-start -->

If you would like to implement solutions that are related to this reference architecture and technologies used you may continue with the following SAP Discovery Center missions:

- [Reduce your CO2 footprint using a smart Generative AI application on SAP BTP](https://discovery-center.cloud.sap/missiondetail/4264/4522/)
<!-- dc-ref-arch-related-missions-end -->
