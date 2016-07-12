---
post_title: Service Discovery and Load Balancing
nav_title: Service Discovery
menu_order: 5
---

DC/OS provides a number of tools out of the box for service discovery and load balancing. Here's an overview of the options, with some general guidelines on what to use in which situations.

| Tool | Type | When should I use it? |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [VIPs][1] ([Minuteman][2]) | Minuteman is a layer 4 load balancer, which can be used for most TCP traffic for any Mesos task within a DC/OS cluster. | When you have internal-only TCP services which do not require layer 7 features. |
| [Marathon-lb (aka MLB)][3] | MLB is an HAProxy based load balancer for Marathon only. | When you need to do external routing or require layer 7 load balancing features. Examples of layer 7 features include: TLS termination, zero-downtime deployments, HTTP sticky sessions, load balancing algorithm customization, network ACLs, HTTP basic auth, gzip compression, and more. |
| [Mesos-DNS][4] | Mesos-DNS is a basic DNS-based service discovery tool that works with any Mesos task. | When neither VIPs nor MLB are adequate, you may use the auto-generated [Mesos-DNS names][5]. For example, to discovery MLB you'd use Mesos-DNS by connecting to MLB with `marathon-lb.marothon.mesos`. Or, if you have UDP services such as StatsD. |

[1]: virtual-ip-addresses/
[2]: load-balancing/
[3]: marathon-lb/
[4]: mesos-dns/
[5]: dns-naming/
