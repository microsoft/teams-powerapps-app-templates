# Add hierarchy to inspection location

The Inspections sample app allows users to create and perform inspections in the app. There are three apps, one per persona to perform, manage, and review Inspections. The three apps are&mdash;Inspections, Manage Inspections and Review Inspections.

By default, the Inspections app is designed for a single store. But what if you perform inspections on multiple stores? You'll want to add a table for stores to the app and let the user select the store in which they are performing inspections so that you can track at which store the inspection was performed.

In this article, we'll learn how to update the app to add a hierarchy of stores so that inspections can be performed for different stores.

Watch this video to learn how to add hierarchy to inspection location: https://www.microsoft.com/videoplayer/embed/RWLkvW

## Prerequisites

To complete this lesson, we'd need the ability to log in into Microsoft Teams that will be available as part of select Microsoft 365 subscriptions, and will also need to have the Inspections sample app for Teams installed. This app can be installed by following these [instructions](../../INSTALLATION.md).

## Edit the Inspections app

1. Login into Teams, and right-click on Power Apps app from the left-pane, and select **Pop out app**.

1. Select **Build** from the top ribbon.

1. Select the team in which the Inspections app is installed.

1. Select Inspections to open the app in Power Apps Studio.

### Add a new table called Store

1. Select **Data** from the left-pane.

1. Select **+ Add data**.

1. Select the **+ Create new table**.

1. Enter table name "Store" and select **Create**.

1. Select the **Add Column** button to add a new column.

1. Enter column name as "Store Number", and select **Create**.

1. Add a few sample records in the table, and select **Close.**

    ![Store Table](https://user-images.githubusercontent.com/122298060/215221836-055df2b4-1921-4c2b-830d-443af9816683.png)

### Update Items screen

Update the formula for the following controls to allow the Items screen to show inspections.

1. Search for and select **lblIssues_Header** label in the **Tree view**.

1. Select the **Text** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    With(
    {
        varDefault: "Issues reported (" & CountRows(
            Filter(
                locSelectedInspection,
                Outcome = 'Inspection Outcome'.Issue
            )
        ) & ")",
        varOOBTextId: "_translateVariable_IssuesHeader",
        varParam0: "(" & CountRows(
            Filter(
                locSelectedInspection,
                Outcome = 'Inspection Outcome'.Issue
            )
        ) & ")"
    },
    ```
    **Add formula section:**
    ```powerapps-dot
    With(
    {
        varDefault: "Issues reported (" & CountRows(
            Filter(
                galInspections.Selected.'Area Inspection Steps',
                Outcome = 'Inspection Outcome'.Issue
            ).'Area Inspection Step'
        ) & ")",
        varOOBTextId: "_translateVariable_IssuesHeader",
        varParam0: "(" & CountRows(
            Filter(
                galInspections.Selected.'Area Inspection Steps',
                Outcome = 'Inspection Outcome'.Issue
            ).'Area Inspection Step'
        ) & ")"
    },
    ```

1. Search for and select **lblNoIssues_Header** label in the **Tree view**.

1. Select the **Text** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    With(
    {
        varDefault: "No issues (" & CountRows(
            Filter(
                locSelectedInspection,
                Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
            )
        ) & ")",
        varOOBTextId: "_translateVariable_NoIssuesHeader",
        varParam0: "(" & CountRows(
            Filter(
                locSelectedInspection,
                Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
            )
        ) & ")"
    },
    ```

    **Add formula section:**
    ```powerapps-dot
    With(
    {
        varDefault: "No issues (" & CountRows(
            Filter(
                galInspections.Selected.'Area Inspection Steps',
                Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
            ).'Area Inspection Step'
        ) & ")",
        varOOBTextId: "_translateVariable_NoIssuesHeader",
        varParam0: "(" & CountRows(
            Filter(
                galInspections.Selected.'Area Inspection Steps',
                Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
            ).'Area Inspection Step'
        ) & ")"
    },
    ```

1. Search for and select **galNoIssuesAttachments** gallery in the **Tree view**.

1. Select the **Items** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    ThisItem.'Area Inspection Images'
    ```

    **Add formula section:**
    ```powerapps-dot
    LookUp('Area Inspection Steps','Area Inspection Step'=ThisItem.'Area Inspection Step').'Area Inspection Images'
    ```

1. Search for and select **galIssuesAttachments** gallery in the **Tree view**.

1. Select the **Items** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    ThisItem.'Area Inspection Images'
    ```

    **Add formula section:**
    ```powerapps-dot
    LookUp('Area Inspection Steps','Area Inspection Step'=ThisItem.'Area Inspection Step').'Area Inspection Images'
    ```

1. Search for and select **galNoIssues** gallery in the **Tree view**.

1. Select the **Items** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    Sort(
    Filter(
        locSelectedInspection,
        Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
    ),
    Value(Sequence),
    Ascending
    )
    ```

    **Add formula section:**
    ```powerapps-dot
    Sort(
    Filter(
        galInspections.Selected.'Area Inspection Steps',
        Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
    ),
    Sequence,
    Ascending
    )
    ```

1. Search for and select **galIssues** gallery in the **Tree view**.

1. Select the **Items** property.

1. Replace the following section of the formula.

    **Remove formula section:**
    ```powerapps-dot
    Sort(
    Filter(
        locSelectedInspection,
        Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
    ),
    Value(Sequence),
    Ascending
    )
    ```

    **Add formula section:**
    ```powerapps-dot
    Sort(
    Filter(
        galInspections.Selected.'Area Inspection Steps',
        Outcome = 'Inspection Outcome'.OK || Outcome = 'Inspection Outcome'.'N/A'
    ),
    Sequence,
    Ascending
    )
    ```

### Add a column to capture Store in the Area Inspections table

1. Select **Data** from the left navigation menu.

1. Locate the **Area Inspections** table, and select **...** (ellipsis).

1. Select **Edit data**.

1. Select **Add Column**, and enter the table name as "Store", type as "Lookup", and related table as "Store".

1. Select **Create**.

1. Select **Close**.

### Add a new screen with a Gallery of Stores

1. Select the Tree view from the left-pane.

1. Select **+ New** screen from the tree view.

1. Select blank layout.

1. Rename the screen to "StoreSelectionScreen".

1. Update the **Fill** property to `gblAppStyles.Background.Fill`.

1. Select **+ Insert** to add a gallery to the new screen.

1. Select **Stores** as the data source.

1. Rename the gallery to "StoresGallery".

1. Set the following properties for the gallery **StoresGallery**.

    | Property | Value |
    | - | - |
    | Template size | 108 |
    | Font size | 20 |
    | Height for Title4 | 45 |
    | Font size for label Subtitle4 | 18 |
    | Height for label Subtitle4 | 45 |

1. Go to the **Items** screen, and copy the **Back** button from the top of the screen.

1. Paste the copied button on the new screen.

1. Repeat the previous steps to copy the label **lblIndividualAreasHeader** from Items screen that reads the text as location to the new screen.

1. Set **Y** property of the label to `btnBackToHome_1.Y+btnBackToHome_1.Height`.

1. Set the following properties of the gallery **StoresGallery**.

    | Property | Value |
    | - | - |
    | Y | `btnBackToHome_1.Height+lblIndividualAreasHeader_1.Height` |
    | Height `Parent.Height-btnBackToHome_1.Height- lblIndividualAreasHeader_1.Height` |
    | OnSelect | `Set(gblSelectedStore,ThisItem);Navigate('Items Screen')` |

1. Go to the Items, select the **Back to home** button on top, and update the following button properties.

    | Property | Value |
    | - | - |
    | OnSelect | `Navigate(StoreSelectionScreen, ScreenTransition.Fade)` |
    | Text | `"Back to Store Selection"` |

1. Go to **Checklist Steps** screen.

1. Select the **OnVisible** property of the screen, and update the patch function for updating the **Area Inspections** app to add the store value in the formula.

    ```powerapps-dot
    , Store: gblSelectedStore
    ```

    ![Add Store to the Patch function](https://user-images.githubusercontent.com/122298060/215221918-a53f97ad-b393-4acc-b8c7-d971f76d68b6.png)


### Update the Welcome Screen navigation

1. From the tree view, select the Welcome Screen.

1. Select the button **Perform an Inspection** (btnInspect).

1. Update the **Navigate** function from the **OnSelect** property of the button so that it takes you to the **StoreSelectionScreen** screen instead of the **Items** screen, with the remaining of the formula unchanged.

   ```powerapps-dot
   Navigate(
   StoreSelectionScreen,
   ScreenTransition.Fade
   );
   ```

    ![Navigate to Store Selection screen](https://user-images.githubusercontent.com/122298060/215221989-6b09231c-f9c6-4af6-a102-cfc9e844d76a.png)

### Publish the Inspections app

All the changes to the Inspections app are completed. The app can now be published by selecting the **Publish to Teams** button on the top-right.

![Publish to Teams](https://user-images.githubusercontent.com/122298060/215222024-3eb4d729-9da1-4abc-8dce-eb93d965b1c0.png)

## Edit the Review Inspections app

1. Open **Power Apps** in Teams.

1. Select **Build** tab from the top ribbon.

1. Select the team in which the Inspections app is installed.

1. Select **Review Inspections** to open the app in the editor.

1. Select **Data** from the left-pane.

1. Select **+ Add** data, and add the **Stores** table to this database for this app.

1. Refresh the **Area Inspections** table so that the **Stores** column shows up in the table.

### Add a label to display the store on the Inspection

1. Open the tree view, and select the Items Screen.

1. Under the group **grpInspectionSteps**, select label called "lblInspection_SubmissionDetails", and update it's **Text** property to the following formula.

    ```powerapps-dot
    If(
        DateDiff(
            Date(
                Year(galInspections.Selected.createdon),
                Month(galInspections.Selected.createdon),
                Day(galInspections.Selected.createdon)
                ),
            Today(),
            Days
                ) = 0,
    If(
        DateDiff(
            Date(
                Year(galInspections.Selected.createdon),
                Month(galInspections.Selected.createdon),
                Day(galInspections.Selected.createdon)
                ),
            Today(),
            Hours
                ) > 0,
        galInspections.Selected.Store.Name & " | Submitted by " &
        galInspections.Selected.createdby.'Full Name' & ", " & DateDiff(
        Date(
            Year(galInspections.Selected.createdon),
            Month(galInspections.Selected.createdon),
            Day(galInspections.Selected.createdon)
            ),
        Today(),
        Hours
                ) & " hrs ago",
    If(
        DateDiff(
            Date(
                Year(galInspections.Selected.createdon),
                Month(galInspections.Selected.createdon),
                Day(galInspections.Selected.createdon)
                ),
        Today(),
        Hours
        ) = 0,
    //"minutes ago"
    galInspections.Selected.Store.Name & " | Submitted by " &
    galInspections.Selected.createdby.'Full Name' & ", minutes ago"
    ,
    If(
        DateDiff(
        Date(
            Year(galInspections.Selected.createdon),
        Month(galInspections.Selected.createdon),
        Day(galInspections.Selected.createdon)
            ),
        Today(),
        Days
        ) = 1,
        //"yesterday",
        galInspections.Selected.Store.Name & " | Submitted by " &
        galInspections.Selected.createdby.'Full Name' & ", yesterday",
        galInspections.Selected.Store.Name & " | Submitted by " &
        galInspections.Selected.createdby.'Full Name' & ", " & DateDiff(
        Date(
            Year(galInspections.Selected.createdon),
            Month(galInspections.Selected.createdon),
            Day(galInspections.Selected.createdon)
            ),
        Today(),
        Days
        ) & " days ago"
    )
    )
    )
    )
    ```

## Test the app

1. Open the Inspections app in the team in which it's installed.

1. Select the Welcome screen from the tree view if running inside Studio, and select **Preview**.

1. Select **Perform an Inspection**.

1. Verify that the Store Selector screen opens.

1. Select a store. The next screen should be the Items screen.

1. Select a location.

1. Select a food inspection checklist on the next screen.

1. Select the button **Begin Inspection**.

1. Answer the questions that are part of the inspection, and then select **Review Inspection**.

1. Select **Submit Inspection** on the next screen.

1. Now, login into the **Review Inspections** app by selecting the **Review Inspection** tab on the top in the team where it's installed.

1. Select the location that you selected earlier to show a list of inspections performed.

1. Select the inspection that was submitted earlier.

1. The screen displays the store name.

    ![Store showing on Location screen](https://user-images.githubusercontent.com/122298060/215222058-abe10838-1834-433d-883c-993b0cc87694.png)

### See also

- [Understand Inspection sample app template architecture](inspection-architecture.md)
- [Customize the Inspection app](customize-inspections.md)
- [Customize sample app templates](https://learn.microsoft.com/en-us/power-apps/teams/customize-sample-apps)
- [Frequently Asked Questions (FAQs) for sample app templates](https://learn.microsoft.com/en-us/power-apps/teams/sample-apps-faqs)
