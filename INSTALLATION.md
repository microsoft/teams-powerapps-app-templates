# App Installation Guide

This document provides instructions on how to download the app package and install the sample app by uploading a [custom app](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) to Teams or [import the app as a solution](https://learn.microsoft.com/en-us/power-apps/teams/import-solution-in-teams) to your Power Apps environment.


## Contents 
1. [Upload the app to Teams as a custom app](#p1)
2. [Import the solution to Power Apps environment](#p2)
---

## Upload the app to Teams as a custom app<a name="p1"></a>
Below are the steps for uploading sample app 'Milestones' as a Teams custom app. You can use similar steps to install other sample apps.
1. Browse to the Releases section of github repository 

![image](https://user-images.githubusercontent.com/84343636/210909295-2cd818b2-c77a-4176-9a8b-f0f76b816956.png)


2. Review the assets for latest release and download the 'AppPackages.zip' file 

![image](https://user-images.githubusercontent.com/84343636/210909692-0a65cf3d-7065-4ee3-ac1d-0269d6aac177.png)

3. Extract the zip file and go to 'Milestones' folder, find the file 'TeamsCustomApp.zip'
![image](https://user-images.githubusercontent.com/84343636/210910318-3ddbcd33-ddbb-44d3-a5c9-0d03f758c47f.png)

4. Go to Teams - Apps - Manage your apps - Click 'Upload an app' - 'Upload a custom app'
![image](https://user-images.githubusercontent.com/84343636/210911499-c30a25ff-4cc8-4147-b475-3494550fc2b9.png)

5. Select the 'TeamsCustomApp.zip' in step 3 and click 'open'
![image](https://user-images.githubusercontent.com/84343636/210911862-12d03758-7f0b-4cb3-a9f0-f252e75f928d.png)

6. A pop-up card should show up, click 'Add to a team' to continue
![image](https://user-images.githubusercontent.com/84343636/210911990-7afff477-7daf-4d3e-982a-be76737c264c.png)

7. Select the Teams team where you want to install the app to and click 'set up tab' to continue
![image](https://user-images.githubusercontent.com/84343636/210912245-68315923-b1aa-47be-be5a-4ef0586d7839.png)

8. Another pop-up card should show up, click 'save' to start the installation
![image](https://user-images.githubusercontent.com/84343636/210912436-9b92b438-63ee-458a-b78c-6e9aaaf49b89.png)

9. Installation of the app begins. Installation might take a while, you can continue with other activities
![image](https://user-images.githubusercontent.com/84343636/210912622-977d484e-8f0f-4d8a-a1a2-4c07064a1170.png)

10. Go back to your teams channel and start use the Milestones app in the tab
![image](https://user-images.githubusercontent.com/84343636/210912785-5e5b0048-506f-49dd-8763-5a8403d58dbc.png)


## Import the solution to Power Apps environment<a name="p2"></a>
Below are the steps for import sample app 'Boards' as a dataverse solution. You can use similar steps to install other sample apps.
You need to have a [Power Apps Teams environment](https://learn.microsoft.com/en-us/power-platform/admin/about-teams-environment) as a prerequisite.

1. Browse to the Releases section of github repository 

![image](https://user-images.githubusercontent.com/84343636/210909295-2cd818b2-c77a-4176-9a8b-f0f76b816956.png)


2. Review the assets for latest release and download the 'AppPackages.zip' file 

![image](https://user-images.githubusercontent.com/84343636/210909692-0a65cf3d-7065-4ee3-ac1d-0269d6aac177.png)

3. Extract the zip file and go to 'Boards' folder, find the file 'DataverseSolution.zip'
![image](https://user-images.githubusercontent.com/84343636/210960158-e1c8f9c3-1821-43b7-bd95-63fa51adb858.png)

4. Open Teams. Go to the Power Apps app within Teams (Install the app from Teams app store if needed) 
![03](https://user-images.githubusercontent.com/84343636/210960240-224a9a54-5bd6-40a7-9b09-07af23847027.jpeg)

5. Browse to the Teams team environment where you’d like to import the solution. Select See All. 
![04](https://user-images.githubusercontent.com/84343636/210960269-fec54f92-8d0f-44bc-85b2-1182f6414534.jpeg)

6. Click the “Import” button. 

![05](https://user-images.githubusercontent.com/84343636/210960307-3f03e9f4-8833-4884-bfae-09bfd7a09c81.jpeg)

7. Browse to the Dataverse Solution file downloaded in step3 and click Next. 

![image](https://user-images.githubusercontent.com/84343636/210960530-6d5ac726-1b77-48f3-935d-4ef7312d5b3a.png)

8. Select the components you want to import (recommended you select all) and click on Import 
![07](https://user-images.githubusercontent.com/84343636/210960585-cfbebdb2-82e7-4873-9171-697d7b9e0e87.jpeg)

The import process will start in background. Import might take a while, you can continue with other activities

9. After solution import, you can view the app's content in 'Installed Apps' - 'See all'
![image](https://user-images.githubusercontent.com/84343636/210960714-6c0e86a0-0673-47f4-96b0-b0fdba1bbe11.png)

10. You can use 'Add to teams' to add the canvas app as a tab in your teams. Refer to [this link](https://learn.microsoft.com/en-us/power-apps/teams/embed-teams-app) for detailed instruction.
![image](https://user-images.githubusercontent.com/84343636/210961683-a46ee0e6-b21d-405d-82ac-a71dbd887519.png)

