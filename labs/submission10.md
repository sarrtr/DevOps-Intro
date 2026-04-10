# Lab 9 submission

## Task 1

### Service names

- AWS’s primary artifact repository service for software packages is AWS CodeArtifact; AWS’s separate container registry is Amazon ECR.
- GCP’s primary registry service is Google Cloud Artifact Registry.
- Azure’s package registry service is Azure Artifacts; Azure’s separate container/OCI registry is Azure Container Registry (ACR).

### Key features and integration capabilities

- AWS CodeArtifact is a managed artifact repository with domains and repositories for org-wide policy, IAM-based access control, and external connections to public sources such as npmjs and Maven Central. It integrates with package tools like npm, Maven, Gradle, nuget, dotnet, twine, and pip, and AWS documents a direct integration with CodeBuild.
- Google Cloud Artifact Registry offers standard, remote, and virtual repositories. Remote repositories can cache upstream sources, and virtual repositories provide a single access point across upstream repos. Google documents IAM-based access control, vulnerability scanning when enabled and supported, and integrations with Cloud Build and Google Kubernetes Engine; Docker clients can authenticate directly as well.
- Azure Artifacts uses feeds to store and share packages while controlling access, and feeds can use upstream sources to pull from public registries or other feeds. Microsoft documents integration with Azure Pipelines for publishing and consuming packages, and feed permissions let you manage access at the feed and view level.

### What each service supports

- AWS CodeArtifact supports Cargo, generic, Maven, npm, NuGet, PyPI, Ruby, and Swift package formats.
- Google Cloud Artifact Registry supports Docker/OCI container images, Helm charts in OCI format, Maven, npm, Python, Apt, Yum, Go, generic artifacts, and Kubeflow pipeline templates.
- Azure Artifacts supports NuGet, npm, Maven, Python, Cargo, and Universal Packages. For container images and OCI artifacts, Azure uses Azure Container Registry, which supports Docker-compatible images, OCI images/artifacts, and Helm charts.

### Comparison table

| Feature | AWS (ECR) | GCP (Artifact Registry) | Azure (ACR) |
|---------|-----------|-------------------------|-------------|
| Artifact Focus | Primarily OCI/Docker Images | Universal (Containers + Language Packages) | Primarily OCI/Docker Images |
| Vulnerability Scanning | Basic (Free), Enhanced (Amazon Inspector - Paid) | On-Demand & Auto (via Container Scanning API - $0.26/image) | Integrated (Microsoft Defender for Containers) |
| Geo-Replication | Cross-region & cross-account | Multi-regional storage | Multi-master geo-replication (Premium tier only) |
| Access Control | IAM Policies | IAM & VPC Service Controls | Azure AD, RBAC, Private Endpoints |
| Automation/Build | Integrated with CodeBuild | Integrated with Cloud Build | ACR Tasks (native build & patching) |
| Pricing Model | Pay-as-you-go (Storage + Data Transfer + Optional Scanning) | Free tier (0.5 GB), Pay-as-you-go (Storage + Data Transfer + Scanning) | Tiered (Basic/Standard/Premium) |
| Unique Strength | Deep AWS ecosystem integration | Unified artifact management across all types | Geo-replication & native ACR Tasks |

### Which registry service would you choose for a multi-cloud strategy and why?

I would choose Google Cloud Artifact Registry because it is the broadest one here because it handles container images and non-container packages in the same service, and it adds standard, remote, and virtual repositories so you can mirror or proxy external sources while centralizing policy and access control. That makes it the most flexible “one registry” option when your build and deployment estate spans more than one cloud.

## Task 2

### Service names

- AWS’s primary serverless compute service is AWS Lambda. It runs code in response to events, supports AWS-managed runtimes plus custom runtimes, and is typically fronted by API Gateway for REST APIs.
- Google Cloud’s primary serverless compute surface is Cloud Run, with Cloud Run functions as the function-style option built on top of it. Cloud Run runs containerized services, while Cloud Run functions handles event-driven or HTTP-triggered functions.
- Azure’s primary serverless compute service is Azure Functions. It runs functions on events, HTTP requests, or schedules, with triggers and bindings for connecting to other services.

### Key features and capabilities

- AWS Lambda is tightly integrated with the AWS event ecosystem. AWS documents native patterns for API Gateway HTTP APIs, S3 events, SQS, and many other event sources; it also offers concurrency controls, Provisioned Concurrency for pre-initialized environments, and SnapStart for sub-second startup in supported runtimes.
- Cloud Run is container-native and more general-purpose than a classic functions runtime. Google describes it as a fully managed platform for code, functions, or containers, with direct VPC connectivity, support for any language in a container, Eventarc triggers for event-driven architectures, and integration with Cloud Build, Artifact Registry, Cloud Deploy, Monitoring, Logging, IAP, and Binary Authorization.
- Azure Functions is built around triggers and bindings, so it connects cleanly to Azure Storage, Cosmos DB, Event Grid, Service Bus, and other services without hardcoding a lot of client plumbing. Azure also supports HTTP-triggered functions for APIs, timer triggers for schedules, and output bindings for writing to queues, databases, and more.

### Supported runtimes and languages

- AWS Lambda supports multiple managed runtimes and custom runtimes. AWS’s runtime docs list current managed runtimes across Node.js, Python, Java, .NET, Ruby, and Go, and AWS also says you can build your own runtime in any programming language.
- Cloud Run is language-agnostic when you deploy containers: you can use any language, framework, or binary. Google also documents source-based deployment support for Go, Node.js, Python, Java, .NET Core, and Ruby.
- Azure Functions officially supports C#, Java, JavaScript, PowerShell, and Python, and Microsoft also documents custom handlers for languages such as Rust and Go.

### Pricing comparison

- AWS Lambda pricing is based on execution duration and memory size, with additional charges for Provisioned Concurrency. AWS measures duration from code start until return or termination, rounded to the nearest millisecond.
- Cloud Run charges only for resources used. Google’s pricing docs show request-based billing with CPU, memory, and request meters, plus a free tier; Cloud Run functions pricing is similarly pay-as-you-go and metered to the nearest 100 ms, with no charge while idle.
- Azure Functions Consumption pricing is based on per-second resource consumption and executions, with a monthly free grant. Flex Consumption adds always-ready instances to reduce cold starts, and Premium is billed per second based on vCPU-seconds and GB-seconds.

### Execution models

- AWS Lambda is fundamentally event-driven, and for HTTP workloads AWS recommends API Gateway or Lambda function URLs. AWS’s API Gateway docs describe REST APIs, HTTP APIs, and WebSocket APIs that can route requests to Lambda.
- Cloud Run supports both HTTP services and event-driven services through Eventarc. Cloud Run functions can be triggered from Google Cloud events, Firebase, Google Assistant, or directly over HTTP. Cloud Run also adds jobs for run-to-completion batch work.
- Azure Functions supports HTTP, event, and scheduled execution models. Microsoft’s docs explicitly describe functions running based on events, in response to HTTP requests, or on a schedule, with triggers and bindings connecting the function to queues, blobs, databases, and other services.

### Cold start characteristics

- AWS Lambda cold starts are real but usually infrequent; AWS says they typically occur in under 1% of invocations and usually range from under 100 ms to over 1 second. AWS recommends Provisioned Concurrency for predictable low latency, and SnapStart can provide sub-second startup in supported runtimes.
- Cloud Run scales from zero, so startup latency can appear when a service or function has been idle. Google recommends minimum instances to reduce cold starts, and its docs explicitly call out long cold start time as a troubleshooting area. Google does not give one universal cold-start number because it depends heavily on image size, runtime, and initialization work.
- Azure Functions Consumption apps can scale to zero when idle, which can introduce startup latency; Microsoft says it mitigates this with prewarmed placeholder functions. Premium uses prewarmed workers and is described as having no delay after being idle.

### Maximum execution duration limits

- AWS Lambda has a hard maximum timeout of 900 seconds, or 15 minutes.
- Cloud Run services allow request timeouts up to 60 minutes. Cloud Run functions likewise supports up to 60 minutes for HTTP-triggered functions, while event-driven functions created with the Cloud Functions v2 API are capped at 9 minutes.
- Azure Functions depends on the hosting plan. Consumption is limited to 10 minutes per execution, while Flex Consumption and Premium do not enforce a maximum execution timeout, though there are grace-period limits during scale-in and platform updates.

### Comparison table highlighting similarities and differences


| Cloud | Primary serverless service(s)  | Main execution model                                | Supported languages/runtimes                                                                     | Cold start posture                                                                                    | Pricing basics                                                                           | Timeout limit                                                                       |
| ----- | ------------------------------ | --------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| AWS   | AWS Lambda                     | Event-driven; HTTP via API Gateway or function URLs | Node.js, Python, Java, .NET, Ruby, Go, plus custom runtimes                                      | Cold starts usually under 1% of invocations; Provisioned Concurrency and SnapStart reduce latency     | Per request + duration + memory; provisioned concurrency extra                           | 15 minutes                                               |                        |
| GCP   | Cloud Run; Cloud Run functions | HTTP services, Eventarc events, batch jobs          | Any language in a container; source-based support for Go, Node.js, Python, Java, .NET Core, Ruby | Scales to zero; minimum instances reduce cold starts                                                  | Pay for used CPU/memory/requests; Cloud Run functions billed by execution time           | 60 minutes for services/HTTP; 9 minutes for event-driven functions                  |    |
| Azure | Azure Functions                | HTTP, events, schedules, bindings                   | C#, Java, JavaScript, PowerShell, Python, custom handlers for Rust/Go                            | Consumption can scale to zero; prewarmed placeholder functions and Premium workers reduce cold starts | Consumption is per execution + time + memory; Premium is per vCPU-seconds and GB-seconds | 10 minutes on Consumption; unbounded on Premium/Flex with plan-specific grace rules |

### Analysis: Which serverless platform would you choose for a REST API backend and why?

I would choose Cloud Run on Google Cloud for a REST API backend. It is natively HTTP-oriented, accepts any language through containers, supports up to 60-minute request timeouts, and gives you strong platform features such as concurrency control, traffic splitting, and direct VPC connectivity. That makes it a very clean fit for a containerized API service.

AWS Lambda is also an excellent REST choice, especially if you are already deep in AWS, but it usually needs API Gateway or function URLs in front of it and still carries Lambda’s 15-minute cap. Azure Functions works well too, but the best cold-start and timeout characteristics depend much more on which hosting plan you choose.

### Reflection: What are the main advantages and disadvantages of serverless computing?

The main advantages are that you do not manage servers, you pay only for what runs, and the platform scales down to zero and up with demand. Serverless also integrates very well with cloud events, queues, storage, and workflows, which makes it a strong fit for APIs, glue code, async processing, and automation.

The main disadvantages are cold starts, hard execution limits, and a stronger dependence on provider-specific triggers, bindings, and integration patterns. Serverless also becomes less attractive for long-running, stateful, or latency-critical workloads unless you use premium features or a different hosting model.