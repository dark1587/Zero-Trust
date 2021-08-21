# Challenges

## Ownership
The major challenge with Zero Trust is ownership. Zero Trust *can* be maintained and owned by a single team in smaller environments, but this does not scale well as an organization grows larger. So, does this go to a centralized team that works with/negotiates with the respective service owners? Or is this owned by an existing team that takes on additional roles/functions? What type of headcount/skillset is needed?

### IAM
Access to applications, and defining is traditionally considered an IAM problem.

### Network
Zero Trust still needs some network connectivity in order for users to access on-premise applications. And depending on your team's roles there will still need to be considerations with storing and maintaing DNS records. In most organizations, connectivity and DNS are likely a Network Engineering function.

### Infrastructure
With many Zero Trust offerings, there is some sort of daemon or agent running inside your infrastructure. Where will this get deployed? Is this on baremetal, VMs, or some sort of Docker/Kubernets service?

### Application Security
App Security needs to be involved to make sure applications (both old and new ones) are able to support standard auth mechanisms, or guide devs away from outdated/unsupported ones.

### SRE/Automation
While during initial tests and deployments can be done manually, as the deployment grows and you're dealing with hundreds or thousands of applications - how does Zero Trust fit within your development lifecycle? Are application deployments self-service or even self-registering? If self-registering, what other process need to be added or updated to support it?

### Application Developers
The devs themselves may be annoyed to have to follow new standards, but this is an opportunity to offer carrots: you want your application reachable by others? You must comply with these standards. If you do, your app will work without VPN and you’ll have far happier customers.
