

![image](https://github.com/Akmeena4u/AZ-900-Bootcamp/assets/93425334/b3424e6e-b56c-42f9-a1d0-bb150a059795)


---



# Deploying a Full Stack Application to Azure App Service - Tutorial

**Introduction:**
Hey, everyone! It's Marina from Sex Muse, and I'm excited to share a new tutorial with you. In this tutorial, I'll guide you through deploying a Full Stack application to Azure App Service. This method is straightforward and involves only 10 steps, making it much simpler than other tutorials I found. Most importantly, it's free! Let's get started!

[Background Music]

**Project Setup:**
To follow along, you can access the project on my [GitHub](link_to_github_repo). The project structure includes a main `server.js` file, a `client` folder with the source code, and more.

**Deployment Steps:**
Now, let's break down the deployment process into 10 steps:

1. **Create Resource Group:**
   - In Azure Portal, create a new Resource Group named "LearnAzureRG" in the West Europe region.

   ```bash
   az group create --name LearnAzureRG --location westeurope
   ```

2. **Create App Service Plan:**
   - Create an App Service Plan named "LearnAzureAppServicePlan" with the Free pricing tier in the same Resource Group.

   ```bash
   az appservice plan create --name LearnAzureAppServicePlan --resource-group LearnAzureRG --sku FREE
   ```

3. **Create App Service (Web App):**
   - Create a Web App named "MeredAzureApp" using the Node.js runtime stack and link it to the created App Service Plan.

   ```bash
   az webapp create --name MeredAzureApp --resource-group LearnAzureRG --plan LearnAzureAppServicePlan --runtime "NODE|14-lts"
   ```

4. **Create GitHub Repository:**
   - On GitHub, create a new repository named "MeredAzureTutorial."

5. **Connect GitHub to Azure:**
   - In Azure Portal, navigate to your App Service and configure continuous deployment with GitHub as the source.

6. **Write Production Script:**
   - Modify `server.js` to include a production script using Express.static to serve static files from the `client/builds` folder.

   ```javascript
   // In server.js
   const express = require('express');
   const path = require('path');
   const app = express();

   // Other routes...

   // Production script
   app.use(express.static(path.resolve(__dirname, 'client/builds')));
   app.get('*', (req, res) => {
       res.sendFile(path.resolve(__dirname, 'client/builds/index.html'));
   });

   // Start server...
   ```

7. **Change Base URL:**
   - Update the base URL in the source code to match the Azure App Service URL (https://yourappname.azurewebsites.net).

   ```javascript
   // In your source code
   const baseURL = 'https://yourappname.azurewebsites.net';
   ```

8. **Build Client Static Files:**
   - In the terminal, navigate to the `client` folder and run `npm run build` to generate static files in the `builds` folder.

   ```bash
   cd client
   npm install
   npm run build
   ```

9. **Push Code to GitHub:**
   - Commit and push the changes, including the updated base URL and the newly created static files.

   ```bash
   git add .
   git commit -m "Updated base URL and built static files"
   git push origin master
   ```

10. **Set Up Environment Variables in Azure:**
    - In Azure Portal, go to the App Service's Configuration settings and add a new application setting for each environment variable (e.g., URI).

**Conclusion:**
Congratulations! You've successfully deployed your Full Stack application to Azure App Service. Now, when you browse your app, you should see it up and running.

Thank you for watching this tutorial. I hope you found it helpful! Let me know if there are any other tutorials you'd like to see.

---

