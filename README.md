## Mastering GitOps : Faster, More Efficient Software Development & Streamlining DevOps Workflows <br/>
## Introduction
[GitOps is a relatively new approach to software development that combines Git](https://applydata.io/gitops-self-healing-services-infrastructure/), the popular version control system, with the automation of DevOps. It emphasizes the use of Git as a single source of truth for both infrastructure and application code, allowing teams to manage their entire development lifecycle from within Git. In this short blog post, we will explore [what GitOps is all about](https://www.gitops.tech/), its key principles, benefits, and how customers can implement it in their organization. <br/>

In Cloud native software development, efficiency and agility are paramount. Traditional methods of software deployment and management often lead to bottlenecks, delays, and inconsistencies. This is where GitOps comes into play. It is a set of practices and principles that utilize version control systems, such as Git, to manage and automate the deployment and operation of applications and infrastructure. [GitOps is a modern approach to software delivery and operations](https://about.gitlab.com/topics/gitops/) that harnesses the power of version control systems, such as Git, to streamline the development and deployment process. GitOps treats infrastructure as code and uses Git as a single source of truth for managing both application code and infrastructure configurations. This means that instead of using separate tools for managing infrastructure and application code, teams can use Git to manage everything from code changes to infrastructure deployments. By doing so, GitOps enables organizations to streamline their development process, improve collaboration between teams, and reduce errors caused by manual processes.<br/>

The [guiding principles of GitOps are simple to articulate from Linux foundations's OpenGitOps landing page](https://github.blog/2023-06-02-applying-gitops-principles-to-your-operations/): A single source of the truth shall be maintained in the Git repository. Automation will be used to apply any changes committed to the Git repository. [Any manual changes to an environment will be reverted automatically](https://opengitops.dev/).In this blog, we will delve into the concept of GitOps, its benefits, and how it is transforming the way organizations manage their software & infrastructure. GitOps focuses on maintaining continuous synchronization or reconciliation between the desired state of the system (defined in Git repositories) and the actual state of the deployed environment. Changes are driven by the state stored in the Git repository.<br/>
## Purpose
Git is a “near universal” ingredient of software development & infrastructure management especially in Cloud native development. However, many customers are missing out on the transformative potential of GitOps due to a lack of understanding. This article aims to bridge the knowledge gap and empower everyone to make informed decisions and unlock the full benefits of GitOps. By embracing GitOps alongside Git and IaC, organizations can uplift their infrastructure provisioning and configuration management processes, achieving unprecedented levels of efficiency, scalability, and collaboration.  <br/> 

One last thing to say before we start : GitOps scales for everyone & customers need not ditch any of their favorite tools. It's about amplifying their power with GitOps principles. Despite “Git” being right there in the name, GitOps doesn’t actually require the use of Git. GitOps doesn’t necessarily involve Git (no, really), nor does it require Kubernetes, the orchestration engine with which it’s regularly paired. Customers that are already invested in other version control software can implement GitOps as well. But Git is widely used with within the devops world to implement CI/CD, so most GitOps projects will end up using Git. GitOps is a way to enable a developer-centric experience for managing applications, [as Weaveworks, the company that coined the term “GitOps,” might say](https://www.weave.works/blog/what-is-gitops-really).<br/>

## Who is this guide for ?

This guide will be helpful for people at all levels and roles. <br/>

1. `Adaptability & Wide Applicability` : All blog's content is designed to be applicable across various roles and experience levels, ensuring relevance for a diverse audience. Both newcomers  and seasoned 
    professionals can benefit from industry standards & insights. <br/>
2. `Fresher's and developers` : For freshers/developers, having an awareness of GitOps can prove beneficial in navigating modern software development projects. Understanding GitOps principles early on can 
    contribute to more seamless collaboration and adherence to best practices.<br/>
3. `Industry Best Practices`: The contents incorporates industry best practices, offering a benchmark to align with and implement in projects. Hence this has wide applicability. <br/>
4. `People working on Proposals/RFP's` : Strengthen proposals with best industry pratices and actionable insights. This guide may belp in creating differentiated offerings with industry best practices. <br/> 

## GitOps in a nutshell.

The below diagrams summarizes GitOps  ([Source : VMWare](https://blogs.vmware.com/cloud/files//2021/02/GitOps-in-a-nutshell.png)) <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/8bdcba54-4767-478e-b410-bc79b0a5e508) <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/c6ab8386-9a68-4ffc-a78c-f8fb5e58d99d)
 <br/><br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/478c503a-d0b8-4fa9-aec7-31eb4e6c7e68) <br/><br/>


[Virtually everything in a GitOps workflow](https://dzone.com/refcardz/the-essentials-of-gitops) related to the software development and deployment process is stored in repository. Embracing GitOps may require a shift in mindset from traditional infrastructure management. Customers/Teams need to adopt a declarative, version-controlled approach to define and manage application & infrastructure, which may be a departure from their existing practices. <br/>
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
* `Automated System State Changes` : Approved changes to the desired state are automatically applied to the system. This principle leverages automation to reduce manual intervention, thus reducing the risk of human error and improving efficiency. It also ensures that system changes are consistently applied across all environments.<br/>
* `Continuous Reconciliation`: The GitOps process continuously monitors and reconciles the actual state of the system with its desired state. This ensures that the system remains in its specified state at all times, and any changes made outside of the Git repository are automatically corrected.<br/>

* `Observability and Auditing` : Observability, which refers to any system that can be observed, is an important concept in GitOps. Observability in GitOps lets customers ensure that the desired state and the observed state (or actual state) are the same. GitOps promotes observability by providing a clear view into changes made to the system over time. Auditing capabilities are inherent in the Git version control system, enabling teams to track who made changes, when, and what those changes were. Any deviations or drifts from the desired state are automatically detected and corrected, maintaining the system's integrity.<br/>
* `Collaboration & Review` : GitOps encourages collaboration between teams, including developers, operations, and quality assurance, to work together on the same codebase. Collaboration is facilitated through pull requests and code reviews within Git. Changes to the system undergo a review process before being merged into the main branch, ensuring that alterations meet quality standards and align with the overall architecture.<br/>
* `Immutable infrastructure` : This builds upon IaC by emphasizing that deployed infrastructure should never be directly modified. Instead, any changes to the desired state are made in the Git repository, triggering a new deployment that replaces the existing infrastructure with the updated version. This ensures that every environment is always in a known, consistent state, free from configuration drift. In GitOps, the concept of immutable infrastructure means that deployed components, whether they are application instances or the underlying infrastructure, are considered immutable. Instead of making changes to existing infrastructure, updates are achieved by replacing the entire instance or environment. <br/>

## GitOps Approaches : Pull Vs Push

GitOps, as a methodology for managing infrastructure and application delivery, offers two distinct approaches: Pull-based and Push-based. Each approach has its characteristics and use cases, catering to different requirements and preferences. Both approaches use Git as the single source of truth for the desired state of the system. However, they differ in how changes to the desired state are applied to the system. <br/><br/>
The pull approach provides better control, governance, and consistency, while the push approach offers simplicity, flexibility, and easier customization. By understanding the differences between these two approaches, developers can make an informed decision on which one is best suited for the project.<br/><br/>
The true benefit of GitOps lies in combining these approaches strategically. Utilize pull-based operators for core infrastructure and application configurations, while leveraging push-based deployments for fast-paced development and experimentation. However there is no thub rule.<br/><br/>
Hybrid Approaches: Many organizations strategically combine pull-based operators for core infrastructure with push-based deployments for fast-paced development. <br/><br/>
Below artciles has details of these approaches and can help anyone decide.<br/>
[Push vs. Pull in GitOps: Is There Really a Difference?](https://thenewstack.io/push-vs-pull-in-gitops-is-there-really-a-difference/)<br/>
[Push vs Pull Deployment](https://coda.io/@kirtan-chavda/gitops/push-vs-pull-deployment-4)<br/>
[GitOps Approach: Pull Vs Push](https://www.devopsschool.com/blog/gitops-approach-pull-vs-push/)<br/>

### Push approach (Agile Interludes)
For nimble teams, iterative development, and rapid deployments, the push approach provides agility and direct control. It is also good for small-scale deployments with less complexity, Teams transitioning to GitOps and leveraging existing CI/CD pipelines & Rapid experimentation and development cycles. <br/>
![image](https://github.com/somrajroy/GitOps/assets/92582005/2e1780a1-4e9f-4e3c-adf0-9f13147dd7b0)<br/>
#### Definition
CI/CD pipelines directly push changes to the target environment : Developer commits changes to Git and CI/CD pipeline builds, tests, and deploys changes to the target environment.<br/>
#### Benefits
  *   Agile experimentation: Enables rapid iterations and quick deployments.
  *   Simpler tooling: Often requires fewer specialized tools.
  *   Direct control: Feels more immediate for those accustomed to hands-on approaches.
### Pull approach

In the pull-based deployment, an operator takes over the deployment pipeline (or more accurately it orchestrates the continuous reconciliation workflow rather than a conventional deployment pipeline). Normally for complex environments, highly regulated deployments, and a desire for declarative control, the pull approach offers stability and resilience. <br/>

![image](https://github.com/somrajroy/GitOps/assets/92582005/ba7d16fa-346f-4d91-b59a-2d2e2923f373) <br/><br/>

#### Definition
 A GitOps operator acts as a vigilant conductor, continuously monitoring a Git repository for changes in desired state : Developer commits changes to Git. Operator detects changes and initiates reconciliation. Operator updates the deployed environment to match the desired state.<br/>

#### Benefits
  *  Declarative: Infrastructure as code ensures clear, repeatable definitions.
  *  Self-healing: Operator automatically reconciles discrepancies, promoting resilience.
  *  Centralized control: Git repository becomes the single source of truth.
  *  Enhanced audit trails: Changes are tracked and versioned in Git.

In summary, the choice between the Push and Pull approaches depends on specific use case, the nature of environment, and security requirements. Both approaches offer advantages and can be used effectively to implement GitOps. <br/><br/>
## GitOps vs CICD
While both GitOps and CI/CD involve using Git to manage changes and automate deployments, they differ in their focus, scope, approach, and key characteristics. While CI/CD is a subset of the software delivery lifecycle focused on automating the build and deployment of applications, GitOps extends these principles to the entire system, encompassing infrastructure, configurations, and application deployment in a declarative and continuous manner. GitOps leverages Git as the central hub for system configuration and state, promoting transparency, auditability, and resilience.<br/><br/>
In essence, CI/CD is a foundation for automated application delivery. GitOps builds upon CI/CD principles and extends them to infrastructure management for a more comprehensive and reliable deployment strategy. GitOps provides a framework for automating infrastructure and application delivery, leveraging Git as the single source of truth and embracing continuous reconciliation. It builds upon CI/CD principles, extending them to infrastructure management and often integrating CI/CD pipelines within its workflows.<br/><br/>

![image](https://github.com/somrajroy/GitOps/assets/92582005/d87d435b-41dd-4cfa-8edc-87c5352a1709)<br/><br/>


## Benefits of GitOps

Automated delivery pipelines roll out changes to application & infrastructure when changes are pushed to Git. But the idea of GitOps goes further than that – it uses tools to compare the actual production state of whole application with what’s under source control and then it highlights when actual state does not match the declared state in Git. GitOps offers several  benefits that contribute to improved development, deployment, and management of applications. Other than what is mentioned in the links of the article, below are some additional benefits. <br/><br/>
* `Improved Disaster Recovery`: As the entire system state is stored in Git, recovering from disasters becomes more manageable. In case of a catastrophic failure, the infrastructure and applications can be 
   quickly redeployed based on the Git repository. <br/>
* `Continuous Delivery and Automation`:  GitOps promotes continuous delivery by automating the deployment process. Changes pushed to the Git repository trigger automated workflows, reducing manual 
     intervention and the likelihood of errors. <br/>
* `Predictable Deployments and Rollbacks`: GitOps allows for predictable and reproducible deployments. If an issue arises, rolling back to a previous known state is as simple as reverting to a specific Git   
   commit.<br/>
* `Traceability and Auditing`: Changes made to the infrastructure and applications are recorded in the Git repository, offering complete traceability. This audit trail is valuable for compliance, debugging, and 
   understanding the history of deployments.<br/>

## Appendix
Below are some additional resources and references for further learning: <br/>

1. [What Are the GitOps Principles and How to Implement Them](https://www.danylkoweb.com/Blog/what-are-the-gitops-principles-and-how-to-implement-them-TB)<br/>
2. [GitOps—From beginner to professional](https://www.site24x7.com/learn/what-is-gitops.html)<br/>
3. [What Is GitOps? How Git Can Make DevOps Even Better](https://codefresh.io/learn/gitops/)<br/>
4. [Git best practices: Workflows for GitOps deployments](https://developers.redhat.com/articles/2022/07/20/git-workflows-best-practices-gitops-deployments#)<br/>
5. [Do You Need GitOps?](https://medium.com/@rze.akbari/do-you-need-gitops-908b797437dc)<br/>
6. [What is GitOps, Practical GitOps CI/CD With Terraform and AWS](https://medium.com/@rkssh-daas/what-is-gitops-practical-gitops-ci-cd-with-terraform-and-aws-4d12a8796da8)<br/>
7. [How to use GitOps to automate Terraform](https://opensource.com/article/23/1/automate-terraform-gitops)<br/>
8. [4 Core Principles of GitOps](https://thenewstack.io/4-core-principles-of-gitops/)<br/>
9. [What Is GitOps](https://octopus.com/blog/what-is-gitops)<br/>
10. [Guide to GitOps and benefits](https://www.weave.works/technologies/gitops/)<br/>
11. [What GitOps and why is it so important](https://www.techtarget.com/searchitoperations/definition/GitOps)<br/>
12. [The benefits of GitOps workflows](https://about.gitlab.com/topics/gitops/gitops-best-practices/)<br/>

