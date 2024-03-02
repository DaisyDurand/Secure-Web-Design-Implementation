# Secure-Web-Design-Implementation

## Description 
This project consists of a custom web application deployed on Microsoft Azure. Utilizing Azure's services, the application is containerized within an Azure Web App and secured with a key vault for sensitive information management. Enhanced security measures include the  implementation of a self-signed certificate, custom Web Application Firewall (WAF) rules, and the configuration of a Front Door instance for global delivery optimization. Security Center recommendations are analyzed and remediated to ensure compliance and mitigate vulnerabilities. The web application itself serves as a blog, providing a platform for content creation publication.

## Environments Used
* Microsoft Azure
## Building a Web Application Lab
### Part 1 - Creation of The Web App

1. Created an Azure account.
  
2. Creating the web app in "App Services":
   
   * Subscription/Resource Group: Azure subscription 1/RedTeam
   * Name: cyberpulseperspectives
   * Publish: Select "Code"
   * Runtime Stack: Select "PHP 8.2"
   * Operating system: Select "Linux"
   * Region: Australia East
  
The web app is called "cyberpulseperspectives" and is created within the "RedTeam" resource group under "Azure subscription 1". The web app is configured to publish code and uses PHP 8.2 as it's runtime stack. This runs on the backend. It operates on a Linux-based operating system and is hosted in the Australia East region for optimal performance and accessiblity. This setup provides a robust platform for hosting and managing PHP-based web applications securely on the Azure cloud infrastructure.
  
3. For the App Service Plan:
   * Under "Pricing Plan", select "Create New" and then enter "project1plan".
   * Select "Basic B1", and then click "Select"
     
5. Select the app. A menu of available options will appear on the left-hand side of the app. Select "Custom domains".
   This is where you will find your unique IP address. A free domain name has been created and the domain is now acessible on the internet.
   
### Part 2 - This is Where The Container is Deployed on The Web App

**Note**: A Docker container was previously added to Docker Hub.

1. Open Azure cloud Shell.
   
2. Configured the web app with the provided container.
   
3. The container has been added and the domain is now accessible.
   
### Part 3 - Designing The Web Application

1. SSH'd over to the container and accessed the HTML and CSS files to design the web page.
 
2. Added:
   
   * Name
   * Email
   * LinkedIn profile link
   * Introduction
   * Profile picture
   * Two custom blogs posts
     
Results:

![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/f910c645-4932-4464-85f6-3c341bee01e2)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/a0e37ff3-c60e-46e0-813f-a81feae7673e)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/13638258-18fa-4d1d-a4f9-9b4dc0551162)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/4d605b41-2536-434a-afac-40915cfe5d3f)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/3e3a408a-5750-484d-997f-1a4718be0357)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/430a80b2-f4d2-46ed-a256-177c31b70e29)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/a19b5f1f-6da9-43ae-ac91-228add0c20fd)
![P1](https://github.com/DaisyDurand/Secure-Web-Design-Implementation/assets/147094227/1b3429a0-010f-474b-8f51-cd54f56e6ed1)

### Part 4 - Create a Key Vault

**Note**: Selected a free Azure domain. Azure provided a trusted certificate for the domain.

1. Select "Key vaults" from the Azure search field.
   
2. Created a key vault:
   
   * Subscription/Resource Group: Azure subscription 1/RedTeam
   * Key Vault Name: project1-KeyVault
   * Region: Australia East
   * Pricing: Standard
     
3. Click next to the Access Configuration Tab
   
   * Vault Access Policy
   * Selected username
     
5. Key vault has been created

There are two types of keys, symmetric keys and asymmetric keys. They are both used for encryption, decryption, authentication and digital signatures. Secrets are things like passwords and API keys. Certificates are digital documents used for authenticating a user’s identity. They bind a public key to an entity to validate the authenticity. An access policy is important on a key vault becuase it prevents unauthorized users or user groups from having access to key vault secrets. The username that was selected defined permissions for that specific user.

### Part 5 - Create a Self-Signed Certificate

Created a self-signed certificate using OpenSSL

1. `openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout project1-key.key -out project1-cert.crt -addext "extendedKeyUsage=serverAuth"`  

   This tells OpenSSL to create an SSL certificate using the sha256 hashing algorithm. The certificate will be valid for one year and uses a 2048-bit RSA key. The outputted name of the private key is project1-key.key and the certificate is project1-cert.crt. The certificate is intended for server authentication. This extenstion of the self-signed certificate ensures aht the certificate can be sued by servers to prove their authencticity when clients connect to them.

3. Certificate information:
   
   * Country Name (2 letterccode) [AU]: CA
   * State or Province Name (full name) [Some State]: Ontario
   * Locality Name (e.g., city) []: Toronto
   * Organization Name (e.g., company) [Internet Widgits Pty Ltd]: Student
   * Organizational Unit Name (e.g., section) []: -
   * Common Name (e.g., server FQDN or YOUR name) []:cyberpulseperspectives.azurewebsites.net
   * Email Address []: -
     
4. The key and certificate have been created. Azure requires a PFX format for its certificates. This format is the combination of the server certificate and the private key in a single encrypted file.
   
5. `openssl pkcs12 -export -out project1-cert.pfx -inkey project1-key.key -in project1-cert.crt`
   
6. This indicates for OpenSSL to create a PFX certificate. The name of the PFX file is "project1-cert.pfx". The current private key that is being imported is "project1-ky.key" and the certificate being imported is "project1-cert.crt".
   
7. The pfx file was downloaded and uploaded to the key vault on Azure. On the "Create a certificate" page select:
   
   * Method of Certificate Creation: Import
   * Certificate Name: project1PFX-cert
   * Upload Certificate File: project1-cert.pfx
   * Password: (password that was used earlier)
     
8. SSL Certificate provided by Azure
   
   Validity: Oct 31, 2023 to June 27, 2024.
   Intermediate certificate: Microsoft Azure TLS Issuing CA 02
   
## Part 6 - Difference between a Self-Signed Certificate and a CA signed Certificate

Self-signed certificates are generated and signed by the entity itself. This means it has not been validated by a trusted third-party Certificate Authority (CA) and diminishes trust from clients. CA-signed certificates undergo a validation process by a trusted CA, e.g. DigiCert. This establishes trust with clients because of the recognition of the CA.

 ## Part 7 - Create a Front Door Instance

 1. Front Door Profile:
    * Front Door: project1-FrontDoor
    * Endpoint name: project1
    * Origin group name: RedTeam
    * Pricing Tier: Premium
      
![image](https://github.com/DaisyDurand/Network-Security/assets/147094227/dc53b5ce-af7b-4211-b3af-35c88d52d847)

## Part 8: Configuring Custom WAF Rule

Name: Project1rule
Priority: 100

Rule's condition:

* Match type: Geo location
* Match variable: Remoteaddr
* Operation: isnot
* Select the three countries (USA, Canada, Australia)
* Then: Deny traffic

![WAF Custom Rule](https://github.com/DaisyDurand/Network-Security/assets/147094227/1789ec0f-7483-483f-8a66-d9e239e2f957)

## Part 9 : Analyzing and Fixing a Security Center Recommendation

The Security Center recommended that "Managed identity should be used in your app". Managed Identity was later enabled  and the necessary permission were granted.
