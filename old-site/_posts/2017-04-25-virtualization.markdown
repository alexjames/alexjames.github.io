# Virtualization

  * Virtualization is the technique of abstracting a resource by using intervening on accesses to that resource. Thus physical resouces 
  are presented as virtual (or logical) resources by the system.
  * 
  
## Containers
  * In large-scale systems, you tend to have multiple VMs, each typically running just on instance of an application. It is expensive to 
  have multiple copies of an application as that implies you need to run multiple VMs. Containers are light-weight a
  * Containers are basically a better abstraction than processes. Processes have their own address space, program state, etc. But they still 
  need OS resources such as files (Ex. /var/etc). Containers encapsulate the traditional process along with its filesystem environment. Thus, a 
  container is a better abstraction than traditional processes. This allows quicker deployment and large-scale migration of applications
  * Processes are an abstraction over the underlying machine hardware. Containers are an abstraction for the application.
