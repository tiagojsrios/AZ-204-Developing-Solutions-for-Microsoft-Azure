# Azure RBAC

Azure role-based access control (Azure RBAC) is an authorization system built on Azure Resource Manager that provides fine-grained access management of resources in Azure. With Azure RBAC, you can grant the exact access that users need to do their jobs.

You grant access by assigning the appropriate Azure role to users, groups, and applications at a certain scope. The scope of a role assignment can be a subscription, a resource group, or a single resource. 

## How does Azure RBAC work?

You control access to resources using Azure RBAC by creating role assignments, which control how permissions are enforced. To create a role assignment, you need three elements: a security principal, a role definition, and a scope.

1. **Security principal (who)**

A security principal is just a fancy name for a user, group, or application that you want to grant access to.

2. **Role definition (what you can do)**

A role definition is a collection of permissions. It's sometimes just called a role. A role definition lists the permissions that can be performed, such as read, write, and delete. Roles can be high-level, like Owner, or specific, like Virtual Machine Contributor.

- **Owner** - Has full access to all resources, including the right to delegate access to others.
- **Contributor** - Can create and manage all types of Azure resources, but can’t grant access to others.
- **Reader** - Can view existing Azure resources.
- **User Access Administrator** - Lets you manage user access to Azure resources.

3. **Scope (where)**

Scope is where the access applies to. Scopes are structured in a parent-child relationship. When you grant access at a parent scope, those permissions are inherited by the child scopes.