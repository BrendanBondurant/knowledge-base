---
type: blog
title: Managing Permissions in Cosmo Just Got Easier with Groups
slug: 2025-07-03-managing-permissions-cosmo-easier-groups
series: WunderGraph Blog
date: 2025-07-03
author: Wilson Rivera
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - Role-Based Access Control
  - API Access Control
  - Developer Experience
  - Security Management
tags:
  - graphql-federation
  - authorization
  - developer-experience
  - security
  - cosmo
entities:
  - Cosmo Groups
  - Role-Based Access Control
  - WunderGraph
  - Cosmo Studio
  - API Keys
summary: |
  Cosmo Groups introduce a new system for managing role-based access control (RBAC) that centralizes permissions across users and API keys. This unified approach replaces scattered configurations with a single model for controlling access to organizations, namespaces, federated graphs, and subgraphs, making permission management and audits significantly easier.
faqs:
  - q: What are Cosmo Groups and why were they introduced?
    a: Cosmo Groups are a new way to manage role-based access control (RBAC) for users and API keys. They were introduced to solve permission inconsistencies, especially for production deployments, and to centralize how access is assigned across namespaces, graphs, and subgraphs.
  - q: How do Groups simplify access control?
    a: Groups let you assign users and API keys to a single set of rules that define what they can see and do. This replaces scattered configurations and legacy UI controls with one unified model, making permission management and audits easier.
  - q: What can I control with Groups?
    a: You can control read and write access to organizations, namespaces, federated graphs, and subgraphs. Roles include Admin, Viewer, Publisher, and others, depending on the resource type. These roles apply to both users and API keys.
  - q: What happens if someone doesn't have access to a resource?
    a: They won't see it. Resources like subgraphs or graphs are hidden in Cosmo Studio, and restricted actions in the CLI will return errors. This ensures a clean and secure developer experience.
  - q: Do existing API keys and users need to be updated?
    a: No immediate action is needed. Existing users and API keys were automatically migrated to groups that match their old permissions. However, it's recommended to start using Groups for better clarity and long-term maintainability.
  - q: Can I assign permissions through the CLI or just in Cosmo Studio?
    a: Both. Groups and their rules can be managed in Cosmo Studio through a role-based resource selector UI. In the CLI, API keys automatically inherit permissions from the group they're assigned to, including publish and deploy capabilities.
canonical_url: https://wundergraph.com/blog/managing-permissions-cosmo-easier-groups
---

When I joined WunderGraph in March, my first full feature was to improve access control in Cosmo, WunderGraph’s platform for managing federated GraphQL APIs.
I didn’t expect the scope to cover so much: frontend, backend, CLI. But the range of changes made it a good opportunity to improve how access control works across the platform.
It's one thing to build something, but another to help define how teams manage who can do what.

Groups introduce a new system for managing [role-based access control (RBAC)](https://cosmo-docs.wundergraph.com/studio/rbac) in Cosmo.
Built to give you more control, especially when your organization gets bigger.

## **Where the Idea Came From**

This began because customers requested more control over their members.
Some needed to restrict publishing access to specific environments, like limiting production deployments to only lead developers.
Others wanted to prevent users from even seeing certain namespaces or subgraphs unless they were explicitly granted access to them.

At the same time, there was inconsistency between user roles and API key permissions.
API keys were managed in a separate interface and always had admin access by default.
That made it harder to limit what automation or external tools could do.
It also meant there was no way to apply the same policies to both users and keys.

Fine-grained GraphQL access control was technically possible before, but it required workarounds and manual setups that didn't scale well.
We needed a centralized and flexible model that could define access rules once and apply them consistently across all systems.

That’s what led us to Groups.

## **What Groups Let You Do**

Groups make it possible to assign roles and resources in one place.
Both members and API keys can be added to a group.
And then, the group defines what they can access.

You can:

* Assign access to specific namespaces, federated graphs, or subgraphs  
* Use different roles for different resources  
* Apply the same permissions to both users and API keys

If someone does not have access to a resource, they won’t even see it in the UI.
Namespaces, graphs, and subgraphs that aren’t assigned to them won’t show up in the sidebar or any of their views.
In the CLI, restricted actions, such as publishing or introspecting, will return errors if the group doesn’t allow them.

## **How Cosmo Groups Work**

You create a Group.
Then you add rules to it.
Each rule links a role to one or more resources.

Important behaviors:

* If a group has no rules, its members and keys have no access.
* If a rule does not specify any resources, it gives access to all.
* If a resource is deleted, the rule falls back to all resources.
* Groups are synchronized through SSO (via OIDC mappers).

Cosmo currently provides the following roles, grouped by category:

### **Organization:**
  *  **Admin**: Provides read and write access to all the organization resources, billing, and settings.
  * **Developer**: Provides read and write access to all organizational resources and read-only access to organizational settings.
  * **API Key Manager**: Provides access to managing the organization's API keys.
  * **Viewer**: Provides read-only access to all the organization resources and settings.
---
### **Namespace:**   
  * **Admin**: Provides write access to the namespace configuration.  
    * When resources are not assigned to this role, members and API keys will be able to create new namespaces
  * **Viewer**: Provides read-only access to the namespace configuration.
    * When resources are not assigned to this role, members and API keys will be able to create new namespaces.
---
### **Graph:**  
  * **Admin**: Provides write access to the graph, like configuring check overrides, creating cache warmer operations and so on.
    * When resources are not assigned to this role, the members and API key will be able to create new graphs.
    * If the role is assigned to a namespace instead of a graph, the members and API keys will be able to create new graphs under that namespace.
  * **Viewer**: Provides read-only access to graph configurations.  
    * When resources are not assigned to this role, the members and API key will be able to create new graphs.
    * If the role is assigned to a namespace instead of a graph, the members and API keys will be able to create new graphs under that namespace.
---
### **Subgraph:**   
  * **Admin**: Provides write access to subgraphs.
    * When resources are not assigned to this role, the members and API key will be able to create and publish any subgraph.
    * If the role is assigned to a namespace instead of a subgraph, the members and API keys will be able to create and publish to any subgraph under that namespace.
  * **Publisher**: Provides write access to subgraphs, but, unlike Admin, members and API keys will not be able to create new subgraphs.
    * When resources are not assigned to this role, the members and API key will be able to publish any subgraph.
    * If the role is assigned to a namespace instead of a subgraph, the members and API keys will be able to publish to any subgraph under that namespace.
  * **Viewer**: Provides read-only access to subgraphs.

Each role type can only be added once per group. For example, you can assign the Admin role to multiple resources, but you can’t assign Admin more than once within the same group.

In [Cosmo Studio](https://cosmo-docs.wundergraph.com/studio/intro), admins use the resource selector UI to assign roles to specific scopes and resources, like namespaces or subgraphs. For example, you can select only the development namespace or a single subgraph within a federated graph. The selector adjusts based on what you pick. If you choose a namespace, it disables individual graph selection. This helps avoid mistakes.

In the CLI, API keys inherit the roles of their group. This means that if a key is added to a group that can publish to a subgraph, that key can be deployed from CI/CD. But if it doesn’t have access, the operation fails.

### Rather than just describing it, let me show you how it works:
{% youtube videoId="Jk84AQKfoCc" /%}

## **What We Had to Build**

We initially went with a hierarchical approach, but it ended up being confusing. If someone had access to a namespace, they also had access to all its graphs. This was not what we wanted. So we removed the hierarchy and made everything explicit.

We iterated over the resource selector a few times. We wanted it to be simple yet also capable of handling complex cases. For example, we had to make sure the selector could handle selecting all graphs in a namespace or just one. We also had to update the sidebar and features to hide content that users don’t have permission to access.

Most of the work was in the backend. But the changes are visible across the entire system. The permission checks are enforced everywhere, including introspection APIs.

We deprecated the separate subgraph member and API key selectors in favor of managing everything through a unified permissions system.

## **Why Groups Make Permissions Easier**

Now you can:

* Assign production access only to specific users or teams.
* Create groups with scoped roles for CI/CD keys, internal devs, or external collaborators.
* Ensure users only see and interact with resources they’ve been granted access to.
* [API Keys](https://cosmo-docs.wundergraph.com/studio/api-keys/api-key-resources) with limited resources will continue to work, but we recommend migrating them to groups.

If you were already using the old system, existing users and keys were automatically placed into groups that reflect their previous permissions.
The legacy roles still work, but using Groups makes management and audits much simpler.

{% partial file="blog-callout.md" /%}

## **My Experience**

This was my first full feature at WunderGraph.
Since it involved access control, there was extra attention on getting the security right.
Once we had aligned on the requirements and structure, implementation moved smoothly.

Groups are now available in Cosmo.
This new RBAC model gives you more flexibility and security across your federated GraphQL setup.
You can manage everything in one place: who can see what, who can publish, and who can create.

[Read the full Cosmo Groups documentation](https://cosmo-docs.wundergraph.com/studio/groups)

Let us know how it works for your team.
I’m especially interested to hear from users with complex environments.

Feel free to open a [discussion](https://github.com/wundergraph/cosmo/discussions) on GitHub or reach out if your team has unique access needs.

---

{% faq /%}

---