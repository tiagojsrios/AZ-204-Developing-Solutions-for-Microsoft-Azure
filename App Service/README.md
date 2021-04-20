# Azure App Service

Azure App Service is a service for hosting web applications, REST APIs, and backend services. App Service is ideal for most websites, particularly if you don't need tight control over the hosting infrastructure. App Service can arrange for multiple instances of the web app to run and will load balance incoming requests across these instances.

## App Service Plan

The App Service plan defines the compute resources your app will consume, where those resources are located, how many additional resources the plan can consume, and the pricing tier. These compute resources are analogous to the server farm in conventional web hosting. One or more apps can be configured to run on the same App Service plan.

Apps in the same App Service plan share the same compute resources. To determine whether the new app has the necessary resources, you need to understand the capacity of the existing App Service plan, and the expected load for the new app.

## Pricing & Reliability

- **Shared compute:** Free and Shared, the two base tiers, run an app on the same Azure VM as other App Service apps, including apps of other customers. These tiers allocate CPU quotas to each app that runs on the shared resources, and the resources cannot scale-out (limit of 165 MB of outbound data per day).

- **Dedicated compute:** Tiers run apps on dedicated Azure VMs. Only apps in the same App Service plan share the same compute resources. The higher the tier, the more VM instances are available to you for scale out.

- **Isolated:** This tier runs dedicated Azure VMs on dedicated Azure virtual networks, which provide network isolation on top of compute isolation to your apps.

## Operating System

Selecting Windows activates the Monitoring tab, where you have the option to enable Application Insights. Enabling this feature will configure your app to automatically send detailed performance telemetry to the Application Insights monitoring service without requiring any changes to your code. Application Insights can be used from Linux-hosted apps as well, but this turnkey, no-code option is only available on Windows.

## Deployment Slots

Within a single Azure App Service web app, you can create multiple deployment slots. Each slot is a separate instance of that web app, and it has a separate hostname.

Use additional slots to host new versions of your web app. Against these instances, you can run tests such as integration tests, acceptance tests, and capacity tests. Fix any problems before you move the code to the production slot.

Each slot shares the resources of the App Service plan, including virtual machine memory and CPU as well as disk space.

If you use ASP.NET to build your app, code is compiled and views are completed when the first user requests a page. Subsequent requests for that page receive a faster response because the code is already compiled.

The initial delay is called a cold start. When you swap a slot into production, you "warm-up" the app because your action sends a request to the root of the site. The warm-up request ensures that all compilation and caching tasks finish.

When you swap two slots, the app's configuration travels to the new slot along with the app. You can override this behavior for individual application settings and configuration strings by configuring them as slot settings.

To help you discover problems before your app goes live into production, Azure App Service offers a swap-with-preview feature. When you choose this option, the swap proceeds in two phases:

- **Phase 1:** Slot settings from the target slot are applied to the web app in the source slot. Then Azure warms up the staging slot. At this point, the swap operation pauses so you can test the app in the source slot to make sure it works with the target slot configuration. If you find no problems, begin the next phase.

- **Phase 2:** The hostnames for the two sites are swapped. The version of the app now in the source slot receives its slot settings.

## Scale Out a Web App

If you select an existing plan, any other web apps that use the same plan will share resources with your web app. They'll all scale together, so they need to have the same scaling requirements. If your apps have different requirements, use a separate App Service plan for each one.

The key to scaling effectively is knowing when to scale, and by how much. You monitor the performance of a web app by using the metrics available for the App Service. The simplest way to do this is to use the Azure portal. If you notice a steady increase in resource use, such as CPU utilization, memory occupancy, or disk queue length, you should consider scaling out before these metrics hit a critical point. You should also monitor the average response time of requests and the number of failing requests.

## Scale Up a Web App

You scale an App Service plan up and down by changing the pricing tier and hardware level that it runs on. You can start with the Free tier and scale up as needed according to your requirements. This process is manual. You can also scale down again if you no longer need the resources associated with a particular tier.

Scaling up can cause an interruption in service to client apps running at the time. They might need to disconnect from the service and reconnect if the scale-up occurs during an active call to the web app. And new connections might be rejected until scaling finishes. Also, scaling up can cause the outgoing IP addresses for the web app to change.