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
2. 
