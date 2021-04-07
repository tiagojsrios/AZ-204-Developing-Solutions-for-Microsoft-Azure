# WebJobs and the WebJobs SDK

WebJobs are a part of the Azure App Service that you can use to run a program or script automatically. There are two kinds of WebJob:

- **Continuous:** These WebJobs run in a continuous loop. For example, you could use a continuous WebJob to check a shared folder for a new photo.

- **Triggered:** These WebJobs run when you manually start them or on a schedule.

These WebJOBS do have a few limitations, such as only supporting ASP.NET / SDK 2.x; however SDK 3.x supports .NET Core.