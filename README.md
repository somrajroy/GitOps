# Understanding GitOps :  A Git-centric framework for continuous deployment for faster, More Efficient Software Development &amp; Streamlining DevOps Workflows<br/>
## Introduction
GitOps is a relatively new approach to software development that combines Git, the popular version control system, with the automation of DevOps. It emphasizes the use of Git as a single source of truth for both infrastructure and application code, allowing teams to manage their entire development lifecycle from within Git. In this short blog post, we will explore what GitOps is all about, its key principles, benefits, and how customers can implement it in their organization. <br/>

In Cloud native software development, efficiency and agility are paramount. Traditional methods of software deployment and management often lead to bottlenecks, delays, and inconsistencies. This is where GitOps comes into play. It is a set of practices and principles that utilize version control systems, such as Git, to manage and automate the deployment and operation of applications and infrastructure. GitOps is a modern approach to software delivery and operations that harnesses the power of version control systems, such as Git, to streamline the development and deployment process. GitOps treats infrastructure as code and uses Git as a single source of truth for managing both application code and infrastructure configurations. This means that instead of using separate tools for managing infrastructure and application code, teams can use Git to manage everything from code changes to infrastructure deployments. By doing so, GitOps enables organizations to streamline their development process, improve collaboration between teams, and reduce errors caused by manual processes.<br/>

The guiding principles of GitOps are simple to articulate: A single source of the truth shall be maintained in the Git repository. Automation will be used to apply any changes committed to the Git repository. Any manual changes to an environment will be reverted automatically.In this blog, we will delve into the concept of GitOps, its benefits, and how it is transforming the way organizations manage their software & infrastructure.<br/>
## GitOps in a nutshell.

The below diagrams summarizes GitOps clearly ([Source : VMWare](https://blogs.vmware.com/cloud/files//2021/02/GitOps-in-a-nutshell.png)) <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/8bdcba54-4767-478e-b410-bc79b0a5e508) <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/c6ab8386-9a68-4ffc-a78c-f8fb5e58d99d)
 <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/478c503a-d0b8-4fa9-aec7-31eb4e6c7e68) <br/><br/>


As per the diagram, virtually everything in a GitOps workflow related to the software development and deployment process is stored in repository. Embracing GitOps may require a shift in mindset from traditional infrastructure management. Customers/Teams need to adopt a declarative, version-controlled approach to define and manage application & infrastructure, which may be a departure from their existing practices. <br/>
* `Infrastructure as Code (IaC)`: These are infra configs (e.g. terraform code). It enables teams to apply version control, collaboration, compliance and CI/CD practices to infrastructure management.<br/>
* `Configurations`: These are the settings and parameters that control the behavior of applications and infrastructure. In a GitOps workflow, configurations are version-controlled and managed alongside the code, ensuring consistency and traceability. <br/>
* `Application code`: This is the actual code of the applications being developed. In GitOps, the application code is maintained in a version control system, often alongside the IaC and configurations, to ensure a unified approach to versioning and changes.<br/>
* `CI/CD pipeline`: CI/CD pipelines define the automated steps that code changes go through from development to production. In GitOps, these pipelines are also treated as code and versioned, allowing for automated, repeatable and reliable processes.<br/>


## Principles of GitOps
The core tenets of GitOps focus on declarative configuration, versioning, collaboration, and automation. It brings together development and operations teams, fostering a unified and efficient approach to continuous delivery. The key principles of GitOps include: <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/1430e5f3-c4b2-4962-a357-77e485a346ad)<br/><br/>

* `Infrastructure as Code (IaC)`: Infrastructure is defined and managed using tools like Terraform, Helm charts, or YAML manifests. These files declaratively state the desired state, making it machine-readable and repeatable.<br/>
* `Versioned and immutable: The canonical desired system state is versioned in Git` : The desired state of the system is stored in a way that enforces immutability, versioning, and retains a complete version history. This principle ensures that all changes are tracked, providing an audit trail and making it easy to roll back to a previous state if necessary. The important thing about this version store is that it is immutable — in other words, it doesn’t change over time. This is great for establishing an audit trail.<br/>
* `Declarative: The entire system has to be described declaratively` : GitOps relies on declarative specifications to define the desired state of both the infrastructure and application components which are stored in Git.  This allows for versioning, collaboration, and easy rollback of infrastructure changes. In the GitOps model, the entire system is configured declaratively. This declarative approach focuses on the outcome (the desired state) rather than the steps required to achieve the desired outcome. GitOps creates state-aware declarative configurations, allowing users to store these states in Git for easy deployment and rollback. <br/>
* `Automation & Automated Synchronization/Deployments` : GitOps workflows include automated processes that continuously synchronize the desired state described in Git with the actual state of the deployed infrastructure. This automation ensures that the system converges towards the declared state & eliminates manual processes and reduces human error.<br/>
* `Continuous Delivery, integration, deployment and Rollback` : GitOps automates the deployment process by integrating CI/CD pipelines with Git workflows. When changes are made to the Git repository, the CI/CD pipeline automatically deploys the changes to the target environment, ensuring consistency and reliability. changes are continuously built, tested, and deployed to production. <br/>
* `Observability and Auditing` : Observability, which refers to any system that can be observed, is an important concept in GitOps. Observability in GitOps lets customers ensure that the desired state and the observed state (or actual state) are the same. GitOps promotes observability by providing a clear view into changes made to the system over time. Auditing capabilities are inherent in the Git version control system, enabling teams to track who made changes, when, and what those changes were. Any deviations or drifts from the desired state are automatically detected and corrected, maintaining the system's integrity.<br/>
* `Collaboration & Review` : GitOps encourages collaboration between teams, including developers, operations, and quality assurance, to work together on the same codebase. Collaboration is facilitated through pull requests and code reviews within Git. Changes to the system undergo a review process before being merged into the main branch, ensuring that alterations meet quality standards and align with the overall architecture.<br/>
* `Immutable infrastructure` : This builds upon IaC by emphasizing that deployed infrastructure should never be directly modified. Instead, any changes to the desired state are made in the Git repository, triggering a new deployment that replaces the existing infrastructure with the updated version. This ensures that every environment is always in a known, consistent state, free from configuration drift. In GitOps, the concept of immutable infrastructure means that deployed components, whether they are application instances or the underlying infrastructure, are considered immutable. Instead of making changes to existing infrastructure, updates are achieved by replacing the entire instance or environment. <br/>

## How GitOps Leverages Version Control Systems (How GitOps Leverages Git for Infrastructure Management)
GitOps leverages version control systems, with Git being the most commonly used, to manage the entire lifecycle of infrastructure and application deployments. By storing infrastructure configurations and deployment manifests in Git, GitOps enables versioning, collaboration, and traceability throughout the development and deployment process.

## GitOps Approaches : Pull Vs Push

GitOps, as a methodology for managing infrastructure and application delivery, offers two distinct approaches: Pull-based and Push-based. Each approach has its characteristics and use cases, catering to different requirements and preferences. Both approaches use Git as the single source of truth for the desired state of the system. However, they differ in how changes to the desired state are applied to the system. <br/><br/>
The pull approach provides better control, governance, and consistency, while the push approach offers simplicity, flexibility, and easier customization. By understanding the differences between these two approaches, developers can make an informed decision on which one is best suited for the project.<br/><br/>
Below artciles has details of these approaches and can help anyone decide.<br/>
[Push vs. Pull in GitOps: Is There Really a Difference?](https://thenewstack.io/push-vs-pull-in-gitops-is-there-really-a-difference/)<br/>
[Push vs Pull Deployment](https://coda.io/@kirtan-chavda/gitops/push-vs-pull-deployment-4)<br/>

### Push approach
For nimble teams, iterative development, and rapid deployments, the push approach provides agility and direct control. <br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/2e1780a1-4e9f-4e3c-adf0-9f13147dd7b0)<br/>

### Pull approach

Normally for complex environments, highly regulated deployments, and a desire for declarative control, the pull approach offers stability and resilience. <br/>

![image](https://github.com/somrajroy/GitOps/assets/92582005/ba7d16fa-346f-4d91-b59a-2d2e2923f373) <br/><br/>

In summary, the choice between the Push and Pull approaches depends on specific use case, the nature of environment, and security requirements. Both approaches offer advantages and can be used effectively to implement GitOps. <br/><br/>

## Benefits of GitOps

Automated delivery pipelines roll out changes to application & infrastructure when changes are pushed to Git. But the idea of GitOps goes further than that – it uses tools to compare the actual production state of whole application with what’s under source control and then it highlights when actual state does not match the declared state in Git. <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/135b5e60-c0e7-450d-bd9c-38c78a441845)
<br/><br/>


