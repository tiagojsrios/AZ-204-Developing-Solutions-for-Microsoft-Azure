# Azure App Service

Azure App Service is a service for hosting web applications, REST APIs, and backend services. App Service is ideal for most websites, particularly if you don't need tight control over the hosting infrastructure.

## App Service Plan

The App Service plan defines the compute resources your app will consume, where those resources are located, how many additional resources the plan can consume, and the pricing tier. These compute resources are analogous to the server farm in conventional web hosting. One or more apps can be configured to run on the same App Service plan.

Apps in the same App Service plan share the same compute resources. To determine whether the new app has the necessary resources, you need to understand the capacity of the existing App Service plan, and the expected load for the new app.

## Pricing & Reliability

- **Shared compute:** Free and Shared, the two base tiers, run an app on the same Azure VM as other App Service apps, including apps of other customers. These tiers allocate CPU quotas to each app that runs on the shared resources, and the resources cannot scale-out (limit of 165 MB of outbound data per day).

- **Dedicated compute:** Tiers run apps on dedicated Azure VMs. Only apps in the same App Service plan share the same compute resources. The higher the tier, the more VM instances are available to you for scale out.

- **Isolated:** This tier runs dedicated Azure VMs on dedicated Azure virtual networks, which provide network isolation on top of compute isolation to your apps.

## Operating System

Selecting Windows activates the Monitoring tab, where you have the option to enable Application Insights. Enabling this feature will configure your app to automatically send detailed performance telemetry to the Application Insights monitoring service without requiring any changes to your code. Application Insights can be used from Linux-hosted apps as well, but this turnkey, no-code option is only available on Windows.