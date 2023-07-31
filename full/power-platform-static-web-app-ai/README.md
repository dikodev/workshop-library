## Build a Community Canvas App with PowerApps
This is a sample static website that can be used to build a static website using Azure Static Web Apps. This site is built using [Hugo](https://gohugo.io/) and is based on the [Hugo Learn Theme](https://learn.netlify.app/en/).

## Prerequisites
1. VS Code 
2. An Azure Subscription

## What students will learn
Smart Shopping Planner is a React application built using JavaScript, that stores data in an Azure SQL database. In this blog, I want to show you how incredibly easy it was to provide REST endpoints (you can work with GraphQL too) to connect the app to the database.

## Lab Milestones

### Milestone 1: Create a new PowerApps Solution
1. Navigate to [PowerApps](https://make.powerapps.com/) and sign in with your Microsoft account.

Make sure that you're in the correct environment at the top right-hand side of the portal - it should look like this: ```(Your name)'s Environment```. If not, click on the environment picker and select the correct environment.

2. Click on **Solutions** in the left navigation pane.

3. Click on **+ New Solution** at the top of the solutions view.

4. In the *New Solution* sidebar, enter a displya name, name (internal name), a publisher and a version for your solution. Only fill in the required fields.

> **Note**: Be aware that the new publisher will have a prefix value. That prefix value will be added to the internal name of every component you create in this solution. When you use 'msft' as a prefix, you will get 'msft_' as a prefix before every component that gets created in the solution.

Use the following values for the required fields:

* Display Name: ```Power Platform + Web Dev Workshop```
* Name: ```PowerPlatformWebDevWorkshop```
* Publisher:  ```create a new one to your own liking and select that one when you are done creating it```
* Version: ```1.0.0.0```

5. Click on **Create** to create your solution.

The solution should automatically open up - If it doesn't, it should appear in the solution list. Click on the display name of your solution to open the solution.

![Screenshot of the solution list](./images/solution-list.png)

### Milestone 2: Creating a new PowerApps Canvas App

1. Click on **+ New** in the top navigation bar of the solution. Hover over *App* menu item and then select **Canvas app**.

The *Canvas App from blank* dialog will pop up.

2. Fill in the following details:

    * App name: ```Community Events```
    * Screen size: ```Tablet```

3. Click on **Create** to create the app.

![Screenshot of the canvas app from blank dialog](./images/canvas-app-from-blank.png)

The Power Apps Studio will open up. When you're here for the first time, a welcome dialog will show. Select the **Skip** button.

### Milestone 3: Adding a Dataverse table as a data source

1. In Power Apps, on the left panel, click the **Data** icon  and click **Add Data**.

![Screenshot of the data panel](./images/data-panel.png)

2. In the ```Select a data source``` window, search for ```CommunityEvents``` and select the result.

3. Click on **Connect** to connect to the data source.

### Milestone 4: Adding a header to the app

With a connection to the Community Events Dataverse table made, you're now ready to configure the UI.

1. First, go back to the ```Tree view```. 

2. Rename the ```Screen1``` screen to ```MainScreen``` by clicking on the ... next to **Screen1** and selecting **Rename**.

3. With the ```MainScreen``` selected, click on the **Insert** tab in the top navigation bar and search for **Container** and select **Vertical Container**.

4. In the ```Tree view```, select the ```Container1``` and rename it to ```ctnMainScreen```.

5. Make sure that the ```ctnMainScreen``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (vertical): ```Start```
        * Align (horizontal): ```Stretch```
        * Gap: ```15```
        * X: ```0```
        * Y: ```0```
        * Height: ```Parent.Height```
        * Width: ```Parent.Witdth```
        * PaddingBottom: ```16```
        * PaddingLeft: ```16```
        * PaddingRight: ```16```
        * PaddingTop: ```16```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * DropShadow: ```None```
        
6. In the ```Tree view```, select the ```ctnMainScreen``` and click on the **Insert** tab in the top navigation bar and search for **Container** and select **Horizontal Container**.

7. In the ```Tree view```, select the ```Container2``` and rename it to ```ctnTableName```.

8. Make sure that the ```ctnTableName``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (horizontal): ```Start```
        * Align (vertical): ```Center```
        * Gap: ```0```
        * Minimum width: ```250```
        * Align in container: ```Stretch```
        * Flexible height: ```0```
        * Height: ```68```
        * PaddingBottom: ```0```
        * PaddingLeft: ```0```
        * PaddingRight: ```0```
        * PaddingTop: ```0```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * Border radius: ```4```
        * DropShadow: ```Light```

9. In the ```Tree view```, select the ```ctnTableName``` and click on the **Insert** tab in the top navigation bar and search for **Label** and select **Label**.

10. In the ```Tree view```, select the ```Label1``` and rename it to ```lblTableName```.

11. Make sure that the ```lblTableName``` is selected and then in the right *Properties Pane*, change the following properties:
        * Text: ```DataSourceInfo(CommunityEvents, DataSourceInfo.DisplayName)```
        * Font size: ```16```
        * Font weight: ```Semibold```
        * Font color: ```RGBA(255, 255, 255, 1)```
        * Font family: ```Segoe UI```
        * Minimum height: ```40```
        * Align in container: ```Stretch```
        * Flexible width: ```1```
        * Minimum width: ```150```
        * PaddingBottom: ```16```
        * PaddingLeft: ```16```
        * PaddingRight: ```16```
        * PaddingTop: ```16```
        * BorderThickness: ```0```
        * Fill: ```RGBA(131, 132, 222, 1)```
        * Border radius: ```0```
        * Focused border: ```0```

### Milestone 5: Adding a Main Body to the app

1. In the ```Tree view```, select the ```ctnMainScreen``` and click on the **Insert** tab in the top navigation bar and search for **Container** and select **Horizontal Container**.

2. In the ```Tree view```, select the ```Container3``` and rename it to ```ctnMainBody```.

3. Make sure that the ```ctnMainBody``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (horizontal): ```Start```
        * Align (vertical): ```Start```
        * Gap: ```16```
        * Minimum width: ```250```
        * Align in container: ```Stretch```
        * Flexible height: ```1```
        * Minimum height: ```100```
        * PaddingBottom: ```2```
        * PaddingLeft: ```2```
        * PaddingRight: ```2```
        * PaddingTop: ```2```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * Border radius: ```0```
        * DropShadow: ```None```

### Milestone 6: Adding a Left Sidebar to the Main Body Container

1. In the ```Tree view```, select the ```ctnMainBody``` and click on the **Insert** tab in the top navigation bar and search for **Container** and select **Vertical Container**.

2. In the ```Tree view```, select the ```Container4``` and rename it to ```ctnLeftSidebar```.

3. Make sure that the ```ctnLeftSidebar``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (vertical): ```Start```
        * Align (horizontal): ```Start```
        * Gap: ```10```
        * Minimum height: ```100```
        * Align in container: ```Stretch```
        * Flexible width: ```If(And(MainScreen.Size = ScreenSize.Small, Or(newMode, editMode, itemSelected)), 0,3)```
        * Fill Portions (Edit in formula bar): ```If(And(MainScreen.Size = ScreenSize.Small, Or(newMode, editMode, itemSelected)), 0,3)```
        * Minimum width: ```250```
        * PaddingBottom: ```0```
        * PaddingLeft: ```16```
        * PaddingRight: ```16```
        * PaddingTop: ```10```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * Border radius: ```4```
        * Border Thickness: ```0```
        * DropShadow: ```Light```
        
4. In the ```Tree view```, select the ```ctnLeftSidebar``` and click on the **Insert** tab in the top navigation bar and search for **Container** and select **Horizontal Container**.

5. In the ```Tree view```, select the ```Container5``` and rename it to ```ctnSearch```.

6. Make sure that the ```ctnSearch``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (horizontal): ```Start```
        * Align (vertical): ```Start```
        * Gap: ```0```
        * Minimum width: ```250```
        * Align in container: ```Stretch```
        * Flexible width: ```0```
        * Minimum height: ```44```
        * PaddingBottom: ```0```
        * PaddingLeft: ```0```
        * PaddingRight: ```0```
        * PaddingTop: ```0```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * Border radius: ```0```
        * Border Thickness: ```0```
        * DropShadow: ```None```

7. In the ```Tree view```, select the ```ctnSearch``` and click on the **Insert** tab in the top navigation bar and search for **Text** and select **Text Input**.

8. In the ```Tree view```, select the ```TextInput1``` and rename it to ```txtSearch```.

9. Make sure that the ```txtSearch``` is selected and then in the right *Properties Pane*, change the following properties:
        * Hint text: ```Search```
        * Default: ```""```
        * Font size: ```14```
        * Font weight: ```Normal```
        * Font color: ```RGBA(0, 0, 0, 1)```
        * Font family: ```Segoe UI```
        * Minimum height: ```44```
        * Align in container: ```Start```
        * Flexible width: ```0```
        * Width: ```320```
        * PaddingBottom: ```5```
        * PaddingLeft: ```12```
        * PaddingRight: ```5```
        * PaddingTop: ```5```
        * BorderThickness: ```1```
        * Fill: ```RGBA(0, 0, 0, 0)```
        * Border radius: ```0```
        * Focused border: ```0```

10. In the ```Tree view```, select the ```ctnLeftSidebar``` and click on the **Insert** tab in the top navigation bar and search for **Icon** and select **Search Icon**.

11. In the ```Tree view```, select the ```Icon1``` and rename it to ```icnSearch```.

12. Make sure that the ```icnSearch``` is selected and then in the right *Properties Pane*, change the following properties:
        * Icon: ```Search```
        * Height: ```44```
        * Align in container: ```Start```
        * Flexible width: ```0```
        * Width: ```44```
        * PaddingBottom: ```10```
        * PaddingLeft: ```10```
        * PaddingRight: ```10```
        * PaddingTop: ```10```
        * BorderThickness: ```0```
        * Fill: ```RGBA(0, 0, 0, 0)```
        * Color: ```RGBA(131, 132, 222, 1)```
        * Border radius: ```0```
        * Focused border: ```2```
    
13. In the ```Tree view```, select the ```ctnLeftSidebar``` and click on the **Insert** tab in the top navigation bar and search for **Container** and select **Horizontal Container**.

14. In the ```Tree view```, select the ```Container6``` and rename it to ```ctnNewRecord```.

15. Make sure that the ```ctnNewRecord``` is selected and then in the right *Properties Pane*, change the following properties:
        * Justify (horizontal): ```Start```
        * Align (vertical): ```Start```
        * Gap: ```0```
        * Minimum width: ```250```
        * Align in container: ```Stretch```
        * Flexible height: ```0```
        * Height: ```44```
        * PaddingBottom: ```0```
        * PaddingLeft: ```0```
        * PaddingRight: ```0```
        * PaddingTop: ```0```
        * BorderThickness: ```0```
        * Fill: ```RGBA(255,255,255,1)```
        * Border radius: ```4```
        * Border Thickness: ```0```
        * DropShadow: ```None```

16. In the ```Tree view```, select the ```ctnNewRecord``` and click on the **Insert** tab in the top navigation bar and search for **Icon** and select **Add Icon**.

17. In the ```Tree view```, select the ```Icon2``` and rename it to ```icnAddRecord```.

18. Make sure that the ```icnAddRecord``` is selected and then in the right *Properties Pane*, change the following properties:
        * Icon: ```Add```
        * OnSelect: ```NewForm(Form1); UpdateContext({ newMode: true });```
        * Height: ```44```
        * Align in container: ```Start```
        * Flexible width: ```0```
        * Width: ```44```
        * PaddingBottom: ```10```
        * PaddingLeft: ```10```
        * PaddingRight: ```10```
        * PaddingTop: ```10```
        * BorderThickness: ```0```
        * Fill: ```RGBA(0, 0, 0, 0)```
        * Color: ```RGBA(131, 132, 222, 1)```
        * Focused border: ```4```

19. In the ```Tree view```, select the ```ctnNewRecord``` and click on the **Insert** tab in the top navigation bar and search for **Label** and select **Label**.

20. In the ```Tree view```, select the ```Label2``` and rename it to ```lblNewRecord```.

21. Make sure that the ```lblNewRecord``` is selected and then in the right *Properties Pane*, change the following properties:
        * Text: ```New```
        * Font size: ```13```
        * Font weight: ```Normal```
        * Color: ```RGBA(0, 0, 0, 1)```
        * Font family: ```Segoe UI```
        * Minimum height: ```44```
        * Align in container: ```Start```
        * Flexible width: ```1```
        * Minimum width: ```150```
        * PaddingBottom: ```5```
        * PaddingLeft: ```5```
        * PaddingRight: ```5```
        * PaddingTop: ```5```
        * BorderThickness: ```0```
        * Fill: ```RGBA(0, 0, 0, 0)```
        * Focused border: ```4```

22. In the ```Tree view```, select the ```ctnLeftSidebar``` and click on the **Insert** tab in the top navigation bar and search for **Rectangle** and select **Rectangle**.

23. In the ```Tree view```, select the ```Rectangle1``` and rename it to ```rectRecordsListSeparator```.

24. Make sure that the ```rectRecordsListSeparator``` is selected and then in the right *Properties Pane*, change the following properties:
        * Minimum width: ```200```
        * Height: ```1```
        * Align in container: ```Start```
        * Flexible Height: ```0```
        * Border Style: ```None```
        * BorderThickness: ```2```
        * Fill: ```RGBA(225, 223, 221, 1)```
        * Focused border: ```4```

25. In the ```Tree view```, select the ```ctnLeftSidebar``` and click on the **Insert** tab in the top navigation bar and search for **Gallery** and select **Vertical Gallery**.

26. In the ```Tree view```, select the ```Gallery1``` and rename it to ```galRecords```.

27. Make sure that the ```galRecords``` is selected and then in the right *Properties Pane*, change the following properties:
        * Items: ```Search('Community Events', txtSearch.Text, "contoso_sessionowner", "cr9be_sessiontitle","contoso_eventstatus")```
        * OnSelect: ```UpdateContext({itemSelected: true, CurrentItem: ThisItem })```
        * Layout: ```Title, Subtitle, Body```
        * Minimum width: ```320```
        * Align in container: ```Stretch```
        * Flexible width: ```1```
        * Minimum height: ```287```
        * BorderThickness: ```0```
        * Fill: ```RGBA(250, 250, 250, 1)```
        * Focused border: ```4```

