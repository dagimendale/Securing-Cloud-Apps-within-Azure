# Creating and Securing a Web App within Azure
In this project I am building, hosting, and designing my own web application, specifically a cyber blog, all within the Azure environment. The preliminary work of this project was just setting up my Azure account with a subscription and resource group, then afterwards further familiarizing myself with the Azure environment.(check prerequisites)

**PART 1A: Creating an Azure Web app**

1. As the two following images reveal, this project begins by typing in "App Services" into the search field and then once within App Services selecting the "+ Create" option.


<img width="420" alt="Screenshot 2024-06-22 150140" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d5dec099-91c7-477d-a120-fbab29fdbc08">
<img width="420" alt="Screenshot 2024-06-22 150452" src="https://github.com/dagimendale/AZUREproject/assets/142032863/9ba446b5-8d75-479e-9f2d-d49741cb9576">


2. Now within the "Basics" section I selected my subscription and my previously created resource group. I then created the domain name, code as the publish option, "PHP 8.2" for the Runtime Stack, Linux for the OS, and the region associated to my resource group. Afterwards, I selected the sevice pricing plan which I put as Basic B1 option and every other section I left as default, leading to me finally selecting the create option. The newly created resource was provided with the cutom domain name we made earlier, as well as a unique IP address.

<img width="420" alt="Screenshot 2024-06-22 150656" src="https://github.com/dagimendale/AZUREproject/assets/142032863/ca1bc3fd-c249-4a97-baeb-15f8cc779397">




<img width="400" alt="Screenshot 2024-06-22 150758" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d952ae75-7e57-43af-ba83-cf74e6c1e1cb">

<img width="424" alt="Screenshot 2024-06-22 184214" src="https://github.com/dagimendale/AZUREproject/assets/142032863/63cfc1a1-851c-481f-99cf-66fe16eed6c4">


**PART 2A: Deploy a Container on the Web App**

Now using azure cloud shell I will deploy a preset [Docker container](https://hub.docker.com/r/cyberxsecurity/project1-apachewebserver) onto my web app, in which contains the framework for the cyber blog webpage I am trying to create.

1. Firstly, I opened Azure Cloud Shell and I entered "az webapp config container set --name bobswebapp --resource-group redteamRG --docker-custom-image-name cyberxsecurity/project1-apachewebserver --enable-app-service-storage -t" into the command line. This command configures my web app with the provided container's settings.
2.To verify the container has been added correctly, I entered "az webapp config container show --name bobswebapp --resource-group redteamRG" into the command line, which shows the container for the web app. 
3. Lastly, I type in the previously created domain to see that the container has been successfully deployed and is ready for customization.


<img width="420" alt="Screenshot 2024-07-03 114637" src="https://github.com/dagimendale/AZUREproject/assets/142032863/5ec08e7c-1470-4b5f-a709-ee6c63b22b2a"> <img width="423" alt="Screenshot 2024-07-03 114826" src="https://github.com/dagimendale/AZUREproject/assets/142032863/359d365a-5c96-4d1b-b821-974a44a97bec"> <img width="388" alt="Screenshot 2024-07-03 115016" src="https://github.com/dagimendale/AZUREproject/assets/142032863/36745b82-0e56-46ac-b373-328fbb11c992">



**PART 3A: Design Your Custom Web App**

After deploying the container that contained the framework the Web App, I am now able to apply my own customizations. First I used SSH to 
<img width="425" alt="Screenshot 2024-07-03 115153" src="https://github.com/dagimendale/AZUREproject/assets/142032863/dfaa26d9-a2c3-4b19-af65-22a9327c2543">
<img width="426" alt="Screenshot 2024-07-03 115341" src="https://github.com/dagimendale/AZUREproject/assets/142032863/eba493b8-9bf5-4269-8c29-1849dd91f5a0">


**Part 1B: Creating a Key Vault**

**Part 2B: Creating a Self-Signed Certificate**

**Part 3B: Analyze a Self-Signed Certificate**

**Part 4B: Analyze a Trusted SSL Certificate**
