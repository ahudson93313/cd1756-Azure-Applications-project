# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

I chose Azure App Service over a Virtual Machine (VM) for my small posting application because it offers clear advantages in cost, scalability, availability, and workflow simplicity for the size and complexity of this application.

1.	Cost: App Service operates on a platform-as-a-service (PaaS) model, which helps keep costs down by handling infrastructure tasks like maintenance and updates. This is more cost-effective for me since this is a small application, as using a VM would mean covering additional expenses for OS management and manual scaling.
2.	Scalability: App Service allows me to scale the application effortlessly with automated options for both vertical and horizontal scaling, based on traffic demands. With a VM, I’d have to manually configure additional instances, load balancers, and resource management, which would require more effort and expertise.
3.	Availability: High availability is built into App Service, with Azure managing failover and redundancy, so I don't need to worry about uptime. Although high availability is possible with VMs, it would mean setting up Availability Sets or Zones, which adds complexity and potentially increases costs.
4.	Workflow: App Service simplifies my workflow with built-in CI/CD support and the ability to deploy directly from source control, making updates seamless. In contrast, using a VM would involve a more complex deployment and maintenance process, with extra steps to configure the server environment.
   
In summary: I chose Azure App Service because it makes deploying, managing, and scaling my application more straightforward and cost-effective. For a small posting app, App Service offers the flexibility and efficiency I need without the added burden of managing server infrastructure, making it an ideal choice for my requirements.


### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

If my application had different requirements, such as the need for more control over the infrastructure or specialized configurations that the App Service cannot easily accommodate, I would consider using a Virtual Machine (VM) instead of an App Service. For example, if my app required specific operating system settings, custom software installations, or advanced networking configurations, a VM would provide the flexibility needed to fully control these elements. Additionally, VMs would be more suitable if I needed to run background tasks or scripts not supported by App Service, or if I required high-performance computing resources and specialized hardware. Other considerations would include setting up Availability Sets or Zones for high availability, configuring load balancers and network security groups for improved security, and implementing a more comprehensive maintenance strategy to handle updates, scaling, and monitoring directly.
