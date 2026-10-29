# Windows Failover Cluster – Simple Demonstration

A practical demonstration of high availability using Windows Failover Clustering and Hyper-V. The project explains how a group of servers can provide shared services and how clustered workloads can be moved to another available node when a node fails or requires maintenance.

> **Scope:** This repository is a learning/demo project. The exact topology, configuration values, and screenshots are documented in the supporting files below. Adapt all settings to your own lab before implementing them.

## Contents

| File | Description |
|---|---|
| [HyperV Failover Cluster.pdf](./HyperV%20Failover%20Cluster.pdf) | Main project document describing the Hyper-V failover-cluster implementation. |
| [Steps Review.pdf](./Steps%20Review.pdf) | Step-by-step review/reference material for the demonstration. |
| [Appendix (System Generated failover report).pdf](./Appendix%20(System%20Generated%20failover%20report).pdf) | System-generated failover report included as supporting evidence. |
| [Screenshots.zip](./Screenshots.zip) | Screenshots captured during the project. |
| [Video demonstration](https://www.youtube.com/watch?v=ssj_Gv378Vc) | Video walkthrough of the project. |

## What is Windows Failover Clustering?

Windows Server Failover Clustering (WSFC) groups multiple servers (nodes) so supported workloads can remain available when a node becomes unavailable. Depending on the configuration, clustered roles can fail over to another eligible node. Hyper-V can use clustering to provide high availability for virtual machines.

Failover helps reduce service interruption, but it does **not** guarantee zero downtime. Results depend on the workload, storage and network design, cluster configuration, and the failure scenario.

## Project objectives

- Demonstrate the basic concept of high availability across cluster nodes.
- Review how clustered workloads can be moved or restarted on another node.
- Observe a failover scenario and retain screenshots and a system-generated report as evidence.
- Provide supporting documentation for learning and lab review.

## Lab prerequisites

Use the PDFs and screenshots in this repository as the authoritative record of the project setup. In general, a comparable lab requires:

- Compatible Windows Server systems configured as cluster nodes.
- Hyper-V installed if virtual machines are the clustered workload.
- Network connectivity for node communication and any required management, storage, or migration traffic.
- A storage design supported by the chosen clustering configuration.
- Administrative access to configure Windows features, validate the cluster, and review events.
- A test workload that is safe to interrupt during a controlled failover exercise.

Exact Windows Server versions, node names, IP addresses, storage configuration, and network layout are not specified in this summary; consult the project documents rather than assuming values.

## Suggested walkthrough

1. **Review the design.** Read [HyperV Failover Cluster.pdf](./HyperV%20Failover%20Cluster.pdf) and identify the nodes, workload, storage, and networks used in the lab.
2. **Prepare the nodes.** Configure the systems and required connectivity according to the documented environment.
3. **Install and configure features.** Enable the required Windows Server Failover Clustering and Hyper-V features, where applicable.
4. **Validate the configuration.** Run the appropriate cluster validation checks before relying on the cluster. Resolve validation errors relevant to the intended design.
5. **Create or review the clustered workload.** Confirm that the workload and its dependencies are configured for the cluster.
6. **Test failover in a controlled lab.** Use the supported cluster management tools to move the role or simulate a planned node outage. Do not perform failure testing on production systems without an approved change plan.
7. **Verify recovery.** Check which node owns the clustered role, whether the workload is accessible, and whether any errors appear in Failover Cluster Manager or Windows event logs.
8. **Record the outcome.** Compare observations with the screenshots and the [system-generated failover report](./Appendix%20(System%20Generated%20failover%20report).pdf).

This is a high-level learning sequence, not a substitute for the configuration steps and values in the included project documents.

## Video demonstration

[![Watch the Windows Failover Cluster demonstration](https://img.youtube.com/vi/ssj_Gv378Vc/hqdefault.jpg)](https://www.youtube.com/watch?v=ssj_Gv378Vc)

[Open the video on YouTube](https://www.youtube.com/watch?v=ssj_Gv378Vc)

## Expected learning outcomes

After reviewing the project, you should be able to explain:

- Why clustering is used to improve workload availability.
- The role of cluster nodes and clustered workloads.
- Why cluster validation and dependency checks matter.
- How to verify a failover using cluster status, workload access, logs, screenshots, and a generated report.
- Why high availability still requires monitoring, testing, backups, and a recovery plan.

## Troubleshooting checklist

If a lab cluster does not behave as expected, review:

- Name resolution, time synchronization, and connectivity between nodes.
- Cluster validation results and relevant Windows event logs.
- Storage visibility and access from the nodes, where shared storage is used.
- Cluster network configuration and firewall rules required by the chosen design.
- Workload dependencies, permissions, and whether the role is configured for failover.
- Whether the destination node has sufficient resources to run the workload.

Use the error messages and validation report to guide troubleshooting; avoid applying generic fixes without understanding the lab topology.

## Safety and production considerations

- Test node failures only in an isolated lab or under an approved maintenance/change window.
- Do not copy IP addresses, credentials, hostnames, or other environment-specific values from a sample into another environment without review.
- Keep Windows Server, Hyper-V, firmware, and drivers supported and updated.
- A cluster is not a replacement for backups, disaster recovery, or application-level resilience.
- Review the security and support requirements for your Windows Server version before deploying a similar design in production.

## References

- [Microsoft Learn: Failover Clustering](https://learn.microsoft.com/en-us/windows-server/failover-clustering/failover-clustering-overview)
- [Microsoft Learn: Hyper-V](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/hyper-v-technology-overview)
- [Project video](https://www.youtube.com/watch?v=ssj_Gv378Vc)

## License

No license is specified in this repository. Unless a license is added, reuse and redistribution are subject to the applicable copyright rules.
