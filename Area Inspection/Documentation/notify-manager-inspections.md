---
title: Notify a manager on completion of an inspection (contains video)
description: Learn about the changes that would be required to notify the manager on completion of an inspection.
author: msftsamperl

ms.topic: conceptual
ms.custom: 
ms.date: 08/16/2021
ms.author: saperlmu
ms.reviewer: mkaur
contributors:
  - joel-lindstrom
  - msftsamperl
  - mduelae
  - sbahl10
---

# Notify a manager on completion of an inspection

The Inspections sample app template allows users to create and perform inspections in the app. There are three apps - one per persona to perform, manage, and review Inspections. The three apps are&mdash;Inspections, Manage Inspections and Review Inspections.

Let’s say you're using inspections to investigate a report of a problem in an area. And for unresolved issues, you want to notify the manager of the person responsible for the area so that they can provide the employee with coaching. In this article, we'll learn how to send a notification to the manager of the person responsible for the location being inspected.

The outcome is that the Inspection app can be used to verify that employees are maintaining an area, and provide notification to management if there are issues. For example, the store manager may want to know if the supervisor of the electronics section of a store is properly maintaining the area of their store and if an issue is found, send their manager an email.

> [!NOTE]
> Before you begin, read [Customize the Inspection app](customize-inspections.md).

Watch this video to learn how to configure manager notification on completion of an inspection: https://www.microsoft.com/videoplayer/embed/RWLn9G

## Prerequisites

To complete this lesson, we'd need the ability to log into Microsoft Teams that will be available as part of select Microsoft 365 subscriptions, and will also need to have the Inspections sample app for Microsoft Teams installed. This app can be installed by following the [installation guide](../../INSTALLATION.md).

## Login into the Manage Inspections app

1. Login into Teams, and select Power Apps from the left-pane.

1. Select **Build** tab from the top.

1. Select **Manage Inspections** to open the app in the editor.

![Select Manage Inspections app](https://user-images.githubusercontent.com/122298060/215219483-96344100-7b33-43e9-895c-829c9f7f3b5d.png)

### Add a new field to the Locations table

Next, we'll add a responsible person column to the location table so we can choose the responsible person for the area.

1. On the Home screen, select **See more** under the **Recent apps** section.
    
    ![Select See more under the Recent apps section](https://user-images.githubusercontent.com/122298060/215219549-6ed3cfa9-f6a4-4886-9289-15c1ab335996.png)


1. Go to the **Installed apps** tab, and select **See all**.

    ![Select See all option](https://user-images.githubusercontent.com/122298060/215219588-8596a6ae-f4fa-4e30-b85e-b38978b4b112.png)

1. Select **Area Inspection Location**.

    ![[Select Area Inspection Location table]](https://user-images.githubusercontent.com/122298060/215219619-6d1641f5-53d1-456f-8886-b001e2f17e04.png)

1. Select **Add Column** on the top-left.

1. Enter the following column details, and then select **Done** to create the **Responsible User** column.

   - Display name – **Responsible User**
   - Data type – **Lookup**
   - Related table – **User**

    ![Add Responsible User column](https://user-images.githubusercontent.com/122298060/215219649-c6782856-cf72-4141-9eae-9b421837a07a.png)

    > [!NOTE]
    > Users must log in to the app one time before they can be selected from the user table.

1. On the **Build** tab under Installed apps, select **Manage Inspections**.

1. Select **Area Inspection Locations** from the left-pane, and then select **Edit**.

    ![Edit Area Inspection Locations Table](https://user-images.githubusercontent.com/122298060/215219688-29a8202b-e110-4409-9318-e34e65a1e255.png)

    The **Responsible User ID** column gets added to the **Area Inspection Locations** table.

1. Update the **Area Inspection Location** with the Responsible User values.

    ![Responsible User column in the Area Inspection Locations table](https://user-images.githubusercontent.com/122298060/215219715-0f0a9642-9eb6-4fa8-81e0-dc1c615c6a29.png)

### Add Responsible User field on the Items Screen on Locations table

Now that we've added the responsible user to the location, we'll now display it on the Items screen.

1. The Responsible User field needs to be added to the Display, Edit, and New sections of the Items Screen. The controls for each of these are all on the same screen but their visibility is controlled by variables. Open the **Items Screen** by selecting it in the Tree view and select the container **conAreaDetails**.

1. Press down the **Ctrl** key, and select the label **Title**.

  ![Copy Title label]https://user-images.githubusercontent.com/122298060/215219759-c2a886c2-73ba-4782-b4c0-4636f83d0d8f.png)

1. Copy the Title label control by highlighting it, and selecting **Ctrl + C** to copy it.

1. Use **Ctrl + V** to paste the label.

1. Update the properties of the new label

    | Property | Value |
    | - | - |
    | Text | “Responsible User” |
    | X | `txtArea_EditTitle.X+txtArea_EditTitle.Width+20` |
    | Y | `If(gblEditLocation \|\| gblAddLocation, 107+150, 61+90)`

1. Rename control to **lblAreaDetails_ResponsibleIUser**.

1. Copy and paste the label that says Backstage and update the properties:

    | Property | Value |
    | - | - |
    | Text | `gblLocation.'Responsible User'.'Full Name'` |
    | X | `txtArea_EditTitle.X+txtArea_EditTitle.Width+20` |
    | Y | `If(gblEditLocation \|\| gblAddLocation, 136+150, 91+90)` |

1. Rename control to **lblArea_ResponsibleUser**.

    The screen then looks like this.

![Responsible User field on Locations screen](https://user-images.githubusercontent.com/122298060/215219815-d9ce781f-2701-4518-b03e-57fe64e5d3b1.png)

1. Press **Alt** key, and select the **Edit** label on the top-right of the **Items** screen. The Title label is same as created above.

1. Copy and paste the textbox that says **Ambient**, and update the properties:

    | Property | Value |
    | - | - |
    | Default | `If(gblAddLocation, "", gblLocation.'Responsible User'.’Full Name’)` |
    | X | `txtArea_EditTitle.X+txtArea_EditTitle.Width+20` |
    | Y | `If(gblEditLocation \|\| gblAddLocation, 136+150, 91+90)` |
    | Hint Text | "Full Name" |
1. Rename control to **txtArea_EditResponsibleUser**.

    The screen then looks like this.

![Locations Screen](https://user-images.githubusercontent.com/122298060/215219835-6d02a08b-0ffc-4d52-83ba-3138e8faee6e.png)

1. Now, press **Alt** key, and select **Cancel** on the top-right. And then press **Alt** key, and select the **Add location** button on the top-left of the **Items** screen.

    ![Select Add Location button](https://user-images.githubusercontent.com/122298060/215219898-68bdaed7-5aac-40ac-b6dc-eb56a62bd41f.png)

1. Verify that the Responsible User label and the textbox show up while adding a new Location.

    The screen then looks like this.

    ![Responsible User field on the Add Location screen](https://user-images.githubusercontent.com/122298060/215219937-531c7e82-da84-48e7-a45e-01bc2388174b.png)
    
1. Select the **Save** button, and on the **OnSelect** property, add the following formula to the Patch functions `, 'Responsible User': txtArea_EditResponsibleUser in the two places shown below -`.

    ![Update patch with Responsible User definition](https://user-images.githubusercontent.com/122298060/215219998-c5d00b94-6ef9-4a84-9d99-3a4cac2c4cc4.png)

![Update second patch with Responsible User definition](https://user-images.githubusercontent.com/122298060/215220023-d376301a-491c-483c-994d-b0aae1b12bb7.png)

Whenever a location is created or updated now, the **Responsible User** value will also be captured and saved on the **Location** record.

### Publish the Manage Inspections app

All the changes to the Manage Inspections app are completed. The app can now be published by selecting the **Publish to Teams** button on the top-right.

![Publish to Teams](https://user-images.githubusercontent.com/122298060/215220058-08fdab11-c915-4c81-9220-00355bd36d33.png)

![Confirm publishing to Teams](https://user-images.githubusercontent.com/122298060/215220087-d61cc570-b484-48be-a26b-336d475cc836.png)

![Add to Channel](https://user-images.githubusercontent.com/122298060/215220120-7a0c06b5-c506-45a7-a5ea-ceb7671d5535.png)

## Edit the inspection app

Now that we've added the field to the Manage Inspections app, we'll create a process to notify the manager of the responsible user when there's an issue.

After publishing the Manage Inspections app, select the **Back** button to go back to the **Build** > **Installed Apps** screen > Select **Inspection**.

![Select Inspection App](https://user-images.githubusercontent.com/122298060/215220160-33273ca4-7d9a-40ee-a1ad-92b5d816ab4a.png)

### Add a Flow to send an Email to the Manager

1. From the Tree View, select the **Review Screen**.

1. Select the **Continue Inspection** (btnContinueSubmitInspection) button.

1. Select the OnSelect property option, copy the entire formula from the formula bar, and then paste it in a text editor.

1. Select the **Continue Inspection** button, and select **...** (ellipsis) on the top, and then select **Power Automate**.
    
    ![Trigger a Flow on the click of Continue Inspection button](https://user-images.githubusercontent.com/122298060/215220210-9fd7c7dd-a9f7-4257-b7a6-cfe04dfc2454.png)

1. Select **+ Create** to create a new flow on [Power Automate](https://flow.microsoft.com).

### Create a Flow to send an email to the Manager of the Responsible User

1. Select the Power Apps trigger from the list.

1. Create the flow **Send Manager Notification of Completion of Inspection**.

1. Select **Ask in Power Apps** option for the **Get Inspection Record** – Row ID step, and for the **Send an Email** – To step.

    ![Flow steps to send notification](https://user-images.githubusercontent.com/122298060/215220257-431007b4-34c5-46a3-8914-ff997c3f29b8.png)

    ![Notification flow send email step](https://user-images.githubusercontent.com/122298060/215220280-69a987f9-a1bb-4c1e-a36d-a619c77dd780.png)

1. Save the flow.

1. Go back to the Power Apps Studio in Teams.

1. Select this flow created from the available flows list. Most likely, the existing formula on the button will get erased out.

1. Update the **Run Flow** formula as shown below.

    ```powerapps-dot
    SendManagerNotificationofCompletionofInspection.Run(If(
    !IsBlank(gblSelectedLocation.'Responsible User'.'Primary Email'),
    Office365Users.ManagerV2(gblSelectedLocation.'Responsible User'.'Primary
    Email').mail
    ),gblLastInspection.'Area Inspection');
    ```

1. Copy the old Continue button formula back from the text editor from Step 3 of the **Add a Flow to send an Email to the Manager** section before the flow formula used in the previous step.

1. Save the app.

### Publish the Inspection app

All the changes to the Inspection app are completed. The app can now be published by selecting the **Publish to Teams** button on the top-right.

![Inspection App Publish to Teams](https://user-images.githubusercontent.com/122298060/215220327-934d98d1-1d07-41d4-8be1-44d53bc54ca3.png)

![Confirm publishing Inspections app to Teams](https://user-images.githubusercontent.com/122298060/215220346-fc0653c1-f6ef-4729-9e16-beced4f165ed.png)

![Add Inspection App to Channel](https://user-images.githubusercontent.com/122298060/215220370-fe9b5d8f-2339-4cee-89c5-22027d705e98.png)

## Verify that a manager exists for the Responsible User

1. Open the link admin.microsoft.com.

1. Select Edit a user.

    ![Verify User has a Manager](https://user-images.githubusercontent.com/122298060/215220406-f776df18-e1c6-4491-82eb-542180f04522.png)

1. Select a User and confirm that the user has a Manager assigned.

    > [!NOTE]
    > If you're working on your organization’s environment, then you'd most likely not need this step. But if working from a trial environment, it is better to create another trial user and add that user as the manager to the Responsible user.

## Test the app

1. Select the Welcome screen from the Tree view in the Editor.

1. Select the **Preview** button to run the app.

    ![Preview Inspection App](https://user-images.githubusercontent.com/122298060/215220453-c47af3e1-1d1a-435c-8ee8-23e77d09381f.png)

1. Select **Perform an Inspection**.

    ![Perform an inspection button](https://user-images.githubusercontent.com/122298060/215220482-ae262db7-6931-45e7-9521-3210523b403c.png)

1. Perform the inspection as shown below.
    
    ![Complete Inspection Demo](https://user-images.githubusercontent.com/122298060/215221002-f1cdbd0a-ad7d-4353-888a-1067ad5d9bad.gif)

    The flow should run after the Submit Inspection button is selected.

1. The easiest way to confirm if the flow ran fine is by opening the Power Automate flow and checking the last run.

   ![Flow run history](https://user-images.githubusercontent.com/122298060/215220574-7f0f3fbc-0175-41fd-bb7d-28bcb1082512.png)

   ![Flow successful run steps](https://user-images.githubusercontent.com/122298060/215220606-38df1a76-cb1b-4a1e-8b1c-55064f6d301d.png)

1. Confirm that the email was sent to the right address by selecting and expanding the Send an email step from the flow results.

    The email received is as shown below.

    ![Email screenshot](https://user-images.githubusercontent.com/122298060/215220668-81f8e604-6157-4c80-803c-1cc71048cc91.png)

### See also

- [Understand Inspection sample app template architecture](inspection-architecture.md)
- [Customize Inspection sample app](customize-inspections.md)
- [Customize sample app templates](https://learn.microsoft.com/en-us/power-apps/teams/customize-sample-apps) <br>
- [Frequently Asked Questions (FAQs) for sample app templates](https://learn.microsoft.com/en-us/power-apps/teams/sample-apps-faqs)
