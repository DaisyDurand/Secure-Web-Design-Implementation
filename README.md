# Secure-Web-Design-Implementation
## Description 
This project consists of a custom web application deployed on Microsoft Azure. Utilizing Azure's services, the application is containerized within an Azure Web App and secured with a key vault for sensitive information management. Enhanced security measures include the  implementation of a self-signed certificate, custom Web Application Firewall (WAF) rules, and the configuration of a Front Door instance for global delivery optimization. Security Center recommendations are analyzed and remediated to ensure compliance and mitigate vulnerabilities. The web application itself serves as a blog, providing a platform for content creation publication.
## Environments Used
* Microsoft Azure
## Building a Web Application Lab
### Part 1 - Creation of The Web App
1. Create an Azure account.
2. In the Azure search field search for "App Services"
3. Select "Create" in the top left had corner.
4. Under the "Basics" tab select:
   * Subscription/Resource Group: select the same subrscription and resource group.
   * Name: This will be the name of the Azure app so choose carefully.
   * Publish: Select "Code"
   * Runtime Stack: Select "PHP 8.0"
   * Operating system: Select "Linux"
   * Region: Select the same region.
5. For the App Service Plan:
   * Under "Pricing Plan", select "Create New" and then enter "project1plan".
   * Select "Basic B1", and then click "Select"
6. Select the "Review + Create" tab.
7. Select "Create" at the bottom of the screen to create your web app.
8. Select "Go to Resource" after the app has been created to find the app.
9. Select the app. A menu of available options will appear on the left-hand side of the app. Select "Custom domains".
   This is where you will find your unique IP address. A free domain name has been created and the domain is now acessible on the internet.
### Part 2 - This is Where The Container is Deployed on The Web App
**Note**: A Docker container was previously added to Docker Hub.
1. Open Azure cloud Shell by clicking on the shell logo in the tool bar. This will be at the top right of the screen.
2. Configured the web app with the provided container.
3. The container has been added and the domain is now accessible.
### Part 3 - Designing The Web Application
1. SSH'd over to the container and accessed the HTML and CSS files to design the web page.
2. Added:
   *Name
   *Email
   *LinkedIn profile link
   *Introduction
   *Profile picture
   *Two custom blogs posts
Results:
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/f910c645-4932-4464-85f6-3c341bee01e2)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/a0e37ff3-c60e-46e0-813f-a81feae7673e)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/13638258-18fa-4d1d-a4f9-9b4dc0551162)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/4d605b41-2536-434a-afac-40915cfe5d3f)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/3e3a408a-5750-484d-997f-1a4718be0357)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/430a80b2-f4d2-46ed-a256-177c31b70e29)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/a19b5f1f-6da9-43ae-ac91-228add0c20fd)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/1b3429a0-010f-474b-8f51-cd54f56e6ed1)
