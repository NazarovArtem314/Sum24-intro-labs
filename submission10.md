# **Lab 10: Cloud Computing Lab - Artifact Registries and Serverless Computing Platforms**
---
## **Task 1: Artifact Registries Research**

1. ***AWS***:
- **CodeArtifact**
    AWS CodeArtifact is a secure, highly scalable, managed artifact repository service that helps organizations to store and share software packages for application development. CodeArtifact can be used with popular build tools and package managers such as NuGet CLI, Maven, Gradle, npm, yarn, pip and twine. CodeArtifact helps reduce the need for you to manage your own artifact storage system or worry about scaling its infrastructure. There is no limit to the number or total size of packages that can be stored in the CodeArtifact repository.
    You can create a connection between your private CodeArtifact repository and an external, public repository, such as npmjs.com or Maven Central. CodeArtifact will then fetch and store packages on demand from the public repository when they're requested by a package manager. This makes it more convenient to consume open-source dependencies used by your application and helps ensure they're always available for builds and development. You can also publish private packages to a CodeArtifact repository. This helps you share proprietary software components between multiple applications and development teams in your organization.

- **AWS ECR**   
    Amazon Elastic Container Registry (Amazon ECR) is an AWS managed container image registry service that is secure, scalable, and reliable. Amazon ECR supports private repositories with resource-based permissions using AWS IAM. This is so that specified users or Amazon EC2 instances can access your container repositories and images. You can use your preferred CLI to push, pull, and manage Docker images, Open Container Initiative (OCI) images, and OCI compatible artifacts.

2. ***GCP***:
- Google Container Registry
    Google Container Registry provides secure, private Docker repository storage on Google Cloud Platform (GCP). You can use gcloud to push repositories to your registry, then you can pull repositories using an HTTP endpoint from any machine, whether it's a Google Compute Engine instance or your own hardware. You pay only for storage and internet egress you use, there is no per-image fee.
    Store your private Docker container images on GCP for fast, scalable retrieval and deployment. Container Registry is a private Docker repository that works with popular continuous delivery systems. It runs on GCP’s Andromeda based network fabric to provide consistent uptime on an infrastructure protected by Google's security. Your private images are stored in Google Cloud Storage and cached in our datacenters, ready to be deployed to Google Container Engine clusters or Compute Engine VMs running Container-Optimized OS. In addition, you can create build pipelines with Google Cloud Build that automatically build and push container images to Container Registry from your source repository on Google Cloud Source Repositories, GitHub, or Bitbucket.

- Google Artifact Registry
    Google Artifact Registry: This service allows for a wider variety of artifact kinds, which extends the capabilities of the Container Registry. Artifact Registry can store and manage a lot of package formats, like Maven, npm, and Python packages, in addition to Docker images. It gives you a centrally controlled, flexible solution for managing all of your software artifacts, and includes additional features for security, artifact management, and CI/CD pipeline integration.

3. ***Azure***:
- Azure Container Registry
    Azure Container Registry (ACR) is a managed Docker container registry service provided by Microsoft Azure. It allows users to store and manage container images for their applications in a secure and scalable manner.
    - ACR integrates seamlessly with other Azure services, such as Azure Kubernetes Service (AKS) and Azure DevOps, enabling efficient deployment and management of containers. 
    - ACR provides a secure and reliable storage solution for Docker container images, allowing users to store and manage their application containers effectively.
    - ACR seamlessly integrates with other Azure services, enabling streamlined deployment and management of containers within the Azure ecosystem.
    - ACR offers robust access control and authentication mechanisms, ensuring the security of container images stored within the registry.
    - ACR delivers high performance and scalability, allowing users to efficiently manage a large number of container images without compromising performance.
    - ACR provides user-friendly management tools accessible through a web interface, command-line interface, and APIs, simplifying the process of managing container images.
    - ACR offers flexible pay-as-you-go pricing, allowing users to optimize costs based on their actual usage of container storage.

- Azure Artifacts
    Azure Artifacts is a service provided by Microsoft Azure that allows developers and organizations to store, publish, and share packages such as NuGet, npm, and Maven artifacts. It is a centralized package management service that helps streamline the process of managing dependencies and packages used in software development projects
    - Azure Artifacts provides a secure and reliable platform for storing and managing packages used in software development, enabling easy access and versioning of dependencies
    - Azure Artifacts seamlessly integrates with Azure DevOps Services, allowing developers to easily incorporate package management into their continuous integration and continuous deployment (CI/CD) pipelines
    - Azure Artifacts offers the ability to create private feeds, ensuring that sensitive or proprietary packages are securely stored and only accessible to authorized users within the organization
    - Azure Artifacts allows developers to track and manage different versions of packages, making it easier to roll back to previous versions if needed
    - Azure Artifacts can act as a proxy for public package registries, caching packages locally to improve build performance and reduce external dependencies.
    - Azure Artifacts provides granular access control settings, allowing organizations to manage permissions and restrict access to specific packages or feeds as needed
    - Azure Artifacts includes search capabilities that make it easy for developers to discover and consume packages from within their development environment
    - Azure Artifacts offers flexible pricing options, allowing organizations to pay for only the storage and data transfer they use, making it a cost-effective solution for managing packages

## **Task 2: Serverless Computing Platform Research**

1. ***AWS***:
- AWS Lambda
    AWS Lambda is a compute service provided by Amazon Web Services (AWS) that allows code to run without infrastructure management. With AWS Lambda, developers can create functions that execute in response to events, such as uploading a file to Amazon S3 or updating a table in Amazon DynamoDB. AWS Lambda scales automatically and only pays for code execution time, making it a convenient and cost-effective tool for event handling and task automation.

2. ***GCP***:
- Google Cloud Functions
    Google Cloud Functions is a scalable pay as you go Functions-as-a-Service (FaaS) offering to run your code with zero server management.
    Google Cloud Functions has a simple and intuitive developer experience. Just write your code and let Google Cloud handle the operational infrastructure. Develop faster by writing and running small code snippets that respond to events and HTTP. Connect to Google Cloud or third-party cloud services via triggers to streamline challenging orchestration problems.

3. ***Azure***:
- Azure Functions
    Azure Functions is a serverless computing service provided by Microsoft Azure. It allows developers to build and deploy event-driven, scalable, and cost-effective applications without the need to manage infrastructure. Here are some key features and benefits of Azure Functions:
    - Azure Functions enables developers to write code that responds to various events, such as HTTP requests, database changes, message queue triggers, timer-based triggers, and more. This event-driven architecture allows for flexible and reactive application development.
    - Azure Functions automatically scales based on the incoming workload. It dynamically allocates resources to handle increased demand and scales down when the workload decreases. This scalability ensures that your application can handle varying levels of traffic without manual intervention.
    - Azure Functions follows a consumption-based pricing model. You only pay for the actual execution time and resources consumed by your functions. This makes it a cost-effective solution, especially for applications with sporadic or unpredictable workloads.
    - Azure Functions seamlessly integrates with other Azure services, such as Azure Storage, Azure Event Hubs, Azure Service Bus, Azure Cosmos DB, and more. This integration allows you to easily build complex workflows and leverage the capabilities of other Azure services within your functions.
    - Azure Functions supports multiple programming languages, including C#, JavaScript, Python, PowerShell, and TypeScript. This flexibility allows developers to choose the language they are most comfortable with and leverage their existing skills and codebase.
    - Azure Functions provides a rich development experience with features like local debugging, continuous integration and deployment (CI/CD) integration, and integration with popular development tools such as Visual Studio and Visual Studio Code. These features enhance developer productivity and streamline the development and deployment process.
    - Azure Functions offers built-in monitoring and diagnostics capabilities. You can monitor the execution and performance of your functions, set up alerts, and gain insights into the health and behavior of your applications. This helps in troubleshooting and optimizing the performance of your functions.

