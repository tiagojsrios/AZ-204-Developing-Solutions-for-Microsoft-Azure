# Chapter 3. Implement Azure security

- When you are working with OAuth2 authentication, remember that you don’t need to store the username and password information in your system. You can delegate that task in specialized authentication servers. Once the user has been authenticated successfully, the authentication server sends an access token that you can use for confirming the identity of the client. This access token needs to be refreshed once the token expires. The OAuth2 can use a refresh token for requesting a new access token without asking the user again for his or her credentials.

- If you plan to work with user delegation SAS, you need to consider that this type of SAS is available only for Azure Blob Storage and Azure Data Lake Storage Gen2. You cannot use either Stored Access Policies when working with user delegation SAS.

- When you are registering a new application in your Azure Active Directory tenant, you need to consider which will be your target user. If you need for any user from any Azure Active Directory organization to be able to log into your application, you need to configure a multitenant app. In those multitenant scenarios, the app registration and management is always performed in your tenant and not in any other external tenant.

- When you are assigning specific service roles, carefully review the permissions granted by the role. In general, granting access to a resource doesn’t grant access to the data managed by that resource. For example, the Storage Account Contributor grants access for managing Storage Accounts but doesn’t grant access to the data itself.

- When you are defining your key-value pair, remember that you are limited to a maximum length of 10,000. Remember also that keys are case-sensitive, so “AppSetting” and “appsetting” are treated as different keys.

- The kind of information that you usually store in an Azure Key Vault is essential information that needs to keep secret, like passwords, connection strings, private keys, and things like that. When configuring the access to your Key Vault, carefully review the access level you grant to the security principal. As a best practice, you should always apply the principle of least privilege. You grant access to the different levels in a Key Vault by creating Access Policies.

- You can configure two different types of managed identities: system- and user-assigned. System-assigned managed identities are tied to the service instance. If you delete the service instance, the system-assigned managed identity is automatically deleted as well. You can assign the same user-assigned managed identities to several service instances.

1. Authentication is the act of proving that a user is who he or she claims to be. 
2. A user authenticates by providing some information that the user only knows. 
3. There are several mechanisms of authentication that provide different levels of security.
4. Some of the authentication mechanisms are form-based, token-based, or certificate-based. 
5. Using form-based authentication requires your application to store your users’ passwords. 
6. Form-based authentication requires HTTPS to make the authentication process more secure. 
7. Using token-based authentication, you can delegate the authorization to third-party authentication providers. 
8. You can add social logins to your application by using token-based authentication.
9. Multifactor authentication is an authentication mechanism that requires the users to provide more than one piece of information that only the user knows. 
10. You can easily implement multifactor authentication by using Azure Active Directory. 
11. There are four main actors in OAuth authentication: client, resource server, resource owner, and authentication server. 
12. The resource owner needs to authenticate the client before sending the authorization grant. 
13. The access token grants access to the resource hosted on the resource server. 
14. The authorization grant or authorization code grants the client the needed rights to request an access token to the authorization server.
15. The client uses the refresh token to get a new access token when it expires without needing to request a new authorization code. 
16. The JSON web token is the most extended implementation of OAuth tokens. 
17. Shared Access Signatures (SAS) is an authentication mechanism for granting access to Azure Storage Accounts without sharing account keys. 
18. Shared Access Signatures (SAS) tokens must be signed. 
19. There are three types of SAS token: user delegation, account, and service SAS. 
20. User delegation SAS tokens are signed using a key assigned to an Azure Active Directory user. 
21. Account and Service SAS are signed using the Azure Storage account key. 
22. You can hide the details of the SAS tokens from the URL by using Stored Access Policies.
23. Shared access signature tokens provide fine-grained access control to your Azure storage accounts. 
24. You can create an SAS token for service, container, and item levels. 
25. You need to register applications in Azure Active Directory for being able to authenticate users using your tenant. 
26. There are three account types supported for authentication: accounts only in the organizational directory, accounts in any organizational directory, and Microsoft accounts. 
27. You need to provide a return URL for authenticating your application when requesting user authentication. 
28. You need to configure a secret or a certificate when your application needs to access information in other APIs. 
29. Role-Based Access Control (RBAC) authorization provides fine-grained access control to the resources. 
30. A security principal is an entity to which you can grant privileges.
31. Security principals are users, groups, service principals, and managed identities. 
32. A permission is an action that a security principal can make with a resource. 
33. A role definition, or role, is a group of permissions. 
34. A scope is a level where you can assign a role. 
35. A role association is a relationship between a security principal, a role, and a scope. 
36. There are four scopes: management groups, subscription, resource group, and resources. 
37. You can centralize the configuration of your distributed application using Azure App Configuration. 
38. Azure App Configuration stores the information using key-value pairs. 
39. Values in the Azure App Configuration are encrypted. 
40. Azure Key Vault provides better security than the Azure App Configuration service. 
41. The limit of size for an Azure App Configuration is 10.000, including the key, label, and value.
42. You can create references from Azure App Configuration items to Azure Key Vault items. 
43. Azure Key Vault allows you to store three types of objects: keys, secrets, and certificates. 
44. You should use managed identities authentication for accessing the Azure Key Vault. 
45. You need to define a certificate policy before creating a certificate in the Azure Key Vault. 
46. If you import a certificate into the Azure Key Vault, a default certificate policy is automatically created for you.
