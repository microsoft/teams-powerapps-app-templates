# How to deploy Inspection app as a broad distribution app

The Inspection sample app for Microsoft Teams is designed to make it easy to track and perform inspections of your assets, equipment, facility, or store.

Watch this video to learn how to deploy Inspection app as a broad distribution app: https://www.microsoft.com/videoplayer/embed/RWLxVt

The inspection solution addresses the following personas:

- **Inspection Manager**: This user creates Inspection forms and manages the list of areas or assets. Inspection Managers use the Manage Inspections app.

- **Inspection Reviewer**: This user reviews and approves submitted inspections. Inspection Reviewers use the Review Inspection app.

- **Inspection User**: This user submits inspections and uses the Inspection app.

You want everyone at in your org, department, or a certain location to be able to submit inspections. These are people outside of the Teams team. We'll share the inspection app with them.

The people responsible for managing and reviewing submitted inspections should be added as members of the team where the app is installed, as these apps are designed to be used from within a team.

> [NOTE]
> By default, when an issue is logged in an inspection, a task is created in Microsoft Planner in the team in which the app is installed, so you should also share access to the Teams Planner environment with the group for which the app is shared for broad distribution.

## Prerequisites

- You must be an owner of the team in which the app is installed to share the app.
- Action required to share an app with colleagues for broad distribution:
    - Share the app with colleagues.
    - Grant security permissions to the tables used in the app.

> [NOTE]
> Aps are installed inside of a tab in a Teams channel. People who develop and extend the app or managers who create or manage the inspection forms should use the app in a team. For people who complete inspections or users who aren't managers, sharing the app with colleagues outside of the team will enable them to use the app without having to be a member of the team.

## Sharing App with Colleagues

This process begins by opening the app in the **Power Apps** app. You may have Power Apps pinned to your Teams App Bar.

1. In Teams, select **…** (ellipsis) from the left-pane.

1. Type **Power Apps** in the search field.

    ![Search for Power Apps](https://user-images.githubusercontent.com/122298060/215221188-08836b6d-b05b-4611-bdda-b92299da5237.png)

1. Select the Power Apps app from the list to open the app. Power Apps will open inside of teams.

1. We recommend that you “pop out” Power Apps so that you won’t lose your app configuration as you move across applications. To pop out the Power Apps app, right-click on the Power Apps logo and select **Pop out app**.

    ![Pop-out app](https://user-images.githubusercontent.com/122298060/215221213-a91def5a-68c0-44ac-a427-75155dcb5f64.png)

1. Right-click on the **Power Apps** logo, and select **Pin** to lock the app to the side menu so it's easy to get to in the future.

    ![Power apps icon](https://user-images.githubusercontent.com/122298060/215221234-c69fd072-578e-4eb4-a3a8-594cc3fed4a6.png)

1. Now that you've loaded the Power Apps app, select **Build**.

    ![Build tab](https://user-images.githubusercontent.com/122298060/215221257-a4e12d71-18c8-44e3-9ee8-e6220201556e.png)

1. This screen will show all the teams that have Power Apps installed in them. Select the team that contain the app you want to share. Select **Share with colleagues**.

    ![Share with colleagues](https://user-images.githubusercontent.com/122298060/215221283-ca60bef0-6291-41c3-ab20-c7973ffcfdba.png)

1. Enter an AD security group or a different team with which you would like to share access to the app.

1. Set the **on/off** toggle to **on** for **Inspection**.

    ![Set security group on for Inspection](https://user-images.githubusercontent.com/122298060/215221320-794c9937-0bd7-402e-a9a1-46762bc35d2c.png)

1. Select **Save**.

## Granting Permissions to the tables

Understanding and assigning permissions to tables are vital to ensure proper security of your shared data. Here are the four permissions available for use.

- **Full Access** – Allows end users to see and edit all records in the table.

    ![Full access feature](https://user-images.githubusercontent.com/122298060/215221355-6211a501-a8bc-4900-a91a-83a8d412a3e9.png)

- **Collaborate** – Allows end users to see all records, but they can only edit their own records.

    ![Collaborate feature](https://user-images.githubusercontent.com/122298060/215221378-e4a9adca-fc78-426b-8524-fe8aa0e6142d.png)

- **Reference** – Provides a read-only view of data for end users.

    ![Reference feature](https://user-images.githubusercontent.com/122298060/215221410-1af4f85c-b1fe-432b-997a-d6cc8cf1186b.png)

- **Private** – Allows end users to only view and edit their own data.

    ![Private feature](https://user-images.githubusercontent.com/122298060/215221426-3f15b69d-7e12-476a-a017-00e7cc421b4f.png)

### Granting permissions to the tables

By default, all of the table permissions for colleagues not in the team are set to **none.** If you leave it that way, colleagues that you share the app with won't be able to use the app, as they won’t have permission to the tables in the app. Follow these steps to set permissions for the tables in the app for
colleagues outside of the team:

1. In Teams, open the **Power Apps** app.

1. Select the **Build** tab.

1. Select the team that contain the app you want to share.

1. Select **Installed apps.** This will show all apps installed in the team.

1. Select **See All** in the **Area Inspection** tile.

    ![See all option for Installed apps](https://user-images.githubusercontent.com/122298060/215221453-1b98b128-6f94-4e0c-8f90-0ad46963af18.png)

1. Select **Tables** from the solution components bar.

1. Select the tables listed individually then **Manage Permissions.**

    ![Manage permissions](https://user-images.githubusercontent.com/122298060/215221539-2990a51a-67f9-49e6-a30f-aaf2491b98fe.png)

1. Select the security group with which the app was shared. The initial permission will show none. Select the desired permission and select **Save.**

1. Repeat step 8 for each additional table in the app.

The following is recommended table permissions:

| Table                          | Permission                                                                                                                                                                                                                                                                                  |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Area Inspection                | Since colleagues outside of your team will need to create their own inspections but not read other users inspections, you should give them **Private** permission for Area Inspection table.                                                                                                |
| Area Inspection Checklist      | Area Inspection Checklist is the header for inspection forms. Since colleagues outside of your team will need to read all inspection checklists but not create or edit records, you should give them **Reference** permission for Area Inspection Checklist table.                          |
| Area Inspection Checklist Step | Area Inspection Checklist Steps are the checklist steps for inspection forms. Since colleagues outside of your team will need to read all inspection checklist step but not create or edit records, you should give them **Reference** permission for Area Inspection Checklist Step table. |
| Area Inspection Group          | Area Inspection Groups aren't actively used in the Inspection app, so you should select **None** for the permission for Area Inspection Group.                                                                                                                                             |
| Area Inspection Image          | Area Inspection Images aren't actively used in the Inspection app, so you should select **None** for the permission for Area Inspection Image.                                                                                                                                             |
| Area Inspection Label          | Since colleagues outside of your team will need to read inspection labels but shouldn't create or edit records, you should give them **Reference** permission for Area Inspection Label table.                                                                                             |
| Area Inspection Locations      | Since colleagues outside of your team will need to read inspection locations but shouldn't create or edit records, you should give them **Reference** permission for Area Inspection Location table.                                                                                       |
| Area Inspection Location Type  | Since colleagues outside of your team will need to read inspection location types but shouldn't create or edit records, you should give them **Reference** permission for Area Inspection Location Type table.                                                                             |
| Area Inspection Settings       | Since colleagues outside of your team will need to read inspection app settings but shouldn't create or edit records, you should give them **Reference** permission for Area Inspection Settings table.                                                                                    |
| Area Inspection Step           | Area Inspection Steps store the user input for inspections. Users will need to be able to create and edit inspection step records, so you should give them **Collaborate** permission on Area Inspection Step table.                                                                        |
| Area Inspection Tasks          | Area inspection tasks are created when users log an issue during an inspection, so you should give them **Collaborate** permission on Area Inspection Task table.                                                                                                                           |
| Area Inspection User Settings  | Since colleagues outside of your team need to create and edit their user setting record for Inspection but shouldn't be able to view or edit other users’ setting records, you should give them **Private** permission to the Area Inspection User Settings table.                         |

### Rename the app

In a large organization, you might have multiple people sharing the same template app with colleagues. If multiple departments are using Inspection, you
can make it easier for your colleagues to find the app by renaming it.

1. Open **Inspection** in Power Apps in Teams.
1. From the designer, in the upper right corner select the app name.
1. Enter a new name for the app. For example, you may want to rename the app **Store Inspection**.
1. Save and publish the app.

## Accessing shared apps

So now that you've shared Inspection with colleagues outside of your team, here's how they'll acquire the app.

1. In Teams, select the eclipses (…) button on left.

1. Select **More apps**.

1. Select **Built for your org**.

1. When the app information screen appears, select **Add** to add the app to the main teams app menu.

    ![Built for your org](https://user-images.githubusercontent.com/122298060/215221582-9451d04d-1493-4947-a29c-7eb402c8a6e0.png)

1. After adding the app to the Teams app menu, select the icon for the app to open it full screen in Teams.

1. If you want to make the app always appear in the app menu so you can easily find it, right-click on the Inspection button on the app menu and select **Pin**.

    ![Pin the app](https://user-images.githubusercontent.com/122298060/215221615-606f49b2-b70f-4ff5-9a28-713eb0da51b8.png)

1. If you would prefer to add the app to another team, select the drop-down by the **Add** button and select **Add to a team**.

    ![Add app to a team](https://user-images.githubusercontent.com/122298060/215221636-4fc6134c-05d6-42f2-a475-a38882b8739a.png)

## Limitation

Currently, Teams apps can only be shared with a single Azure Active Directory group.

### See also

- [Understand Inspection sample app architecture](inspection-architecture.md)
- [Customize Inspection app](customize-inspections.md)
- [Sample apps FAQs](sample-apps-faqs.md)
- [Use sample apps from the Teams store](use-sample-apps-from-teams-store.md)
