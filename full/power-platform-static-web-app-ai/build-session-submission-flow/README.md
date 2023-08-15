## Build Community Event Submission and Management Flows with Power Automate

## Prerequisites
1. VS Code 
2. An Azure Subscription

## What students will learn
Smart Shopping Planner is a React application built using JavaScript, that stores data in an Azure SQL database. In this blog, I want to show you how incredibly easy it was to provide REST endpoints (you can work with GraphQL too) to connect the app to the database.

## Lab Milestones

### Milestone 1: Create a Submission Flow with Power Automate

1. Click **+ New** in the top navigation bar of the solution. Hover over **Automate** and hover over **Cloud Flow**. Select **Automated**.

    ![Screenshot of the Power Automate menu with the Automated option highlighted](images/01.png 'Power Automate menu')

2. In the popup dialog box, enter the following details.

    - **Flow name**: `Session Approval Flow`
    - **Trigger**: `When a row is added, modified or deleted`

    ![Screenshot of the Power Automate dialog box with the details filled in](images/02.png 'Power Automate dialog box')

3. Click **Create**.

4. In the **When a row is added, modified or deleted** trigger, click **Add an action**.

    ![Screenshot of the Power Automate trigger with the Add an action button highlighted](images/03.png 'Power Automate trigger')

5. Once the flow opens, update the trigger with the following details.

    - **Change Type**: `Added`
    - **Table name**: `Community Events`
    - **Scope**: `Organization`

    ![Screenshot of the Power Automate trigger with the details filled in](images/04.png 'Power Automate trigger')

6. Click **+ New step**.

7. In the **Choose an action** dialog box, search for **AI Builder** and select **Create text with GPT (preview)**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/05.png 'Power Automate dialog box')

8. In the **Create text with GPT (preview)** action, click **Create Prompt**.

    ![Screenshot of the Power Automate action with the Create Prompt button highlighted](images/06.png 'Power Automate action')

9. In the **Create prompt** dialog box, choose **Summarize text** then click on **Use Prompt in flow**.

    ![Screenshot of the Power Automate dialog box with the Summarize text option highlighted](images/07.png 'Power Automate dialog box')

10. In the **Create text with GPT (preview)** action, remove the text **##Include text here** and replace it with the following.

    ```
    ## @{triggerOutputs()?['body/sessionowner']} has requested to be part of the upcoming community calls by hosting a session on @{triggerOutputs()?['body/sessiontitle']}. The session is about @{triggerOutputs()?['body/sessiondescription']}
    ```

    ![Screenshot of the Power Automate action with the text filled in](images/08.png 'Power Automate action')

11. Click **+ New step**.

12. In the **Choose an action** dialog box, search for **Approvals** and select **Start and wait for an approval**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/09.png 'Power Automate dialog box')

13. In the **Start and wait for an approval** action, update it with following details.

    - **Approval type**: `Approve/Reject - First to respond`
    - **Title**: `Approval Request for New Session`
    - **Assigned to**: `enter desired email address`
    - **Details**: `Hi Community Manager,
    
    We have a new request for our community calls session, below is a few details partaining to the request.
    
    Request Summary: @{outputs('Create_text_with_GPT_(preview)')?['body/responsev2/predictionOutput/text']}`

    Original Request: 
    Session Title: @triggerOutputs()?['body/sessiontitle']
    Session Description: @triggerOutputs()?['body/sessiondescription']
    Session Owner: @triggerOutputs()?['body/sessionowner']
    Session Date: @triggerOutputs()?['body/sessiondate']

    ![Screenshot of the Power Automate action with the details filled in](images/10.png 'Power Automate action')

    > **Note**: You can use the **Add dynamic content** button to add the dynamic content to the **Details** field.

14. Click **+ New step**.

15. In the **Choose an action** dialog box, search for **Control** and select **Condition**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/11.png 'Power Automate dialog box')

16. In the **Condition** action, update it with following details.

    - **Choose a value**: `Add the dynamic content Responses Approver Response`
    - **Choose a condition**: `is equal to`
    - **Choose a value**: `Approve`

    ![Screenshot of the Power Automate action with the details filled in](images/12.png 'Power Automate action')

17. Click **Add an action** inside the **If/yes** branch.

18. In the **Choose an action** dialog box, search for **Dataverse** and select **Update a row**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/13.png 'Power Automate dialog box')

19. In the **Update a row** action, update it with following details.

    - **Table name**: `Community Events`
    - **Row ID**: `Add the dynamic content Row ID (normally tied to the name of the table)`
    - **Session Status**: `Approved`

    ![Screenshot of the Power Automate action with the details filled in](images/14.png 'Power Automate action')

20. Click **+ New step**.

21. In the **Choose an action** dialog box, search for **Office 365 Outlook** and select **Send an email (V2)**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/15.png 'Power Automate dialog box')

22. In the **Send an email (V2)** action, update it with following details.

    - **To**: `Add the dynamic content Session Owner`
    - **Subject**: `Your session has been approved!`
    - **Body**: `Hi @{triggerOutputs()?['body/sessionowner']},

    We are happy to inform you that your session has been approved. Please see below for the details of your session.

    Session Title: @{triggerOutputs()?['body/sessiontitle']}
    Session Description: @{triggerOutputs()?['body/sessiondescription']}
    Session Owner: @{triggerOutputs()?['body/sessionowner']}
    Session Date: @{triggerOutputs()?['body/sessiondate']}

    We look forward to seeing you at the event!

    Best Regards,
    Community Manager`

    ![Screenshot of the Power Automate action with the details filled in](images/16.png 'Power Automate action')

Milestone 1 is now complete. Click **Save** in the top navigation bar of the flow.

## Milestone 2: Create a flow to send an email updates to Community Members for upcoming sessions

In this milestone, you'll create a flow that sends an email to the session owner when the session is rejected.

1. Click **+ New** in the top navigation bar of the solution. Hover over **Automate** and hover over **Cloud Flow**. Select **Instant**.

    ![Screenshot of the Power Automate dialog box with the details filled in](images/17.png 'Power Automate dialog box')

2. In the **Create a flow** dialog box, update the flow with the following details.

    - **Flow name**: `Send email updates to Community Members for upcoming sessions`
    - **Flow type**: `Instant - from blank`

    ![Screenshot of the Power Automate dialog box with the details filled in](images/18.png 'Power Automate dialog box')

3. Click **Create**.

4. In the **Flow Designer**, click **+ New step** after your trigger.

5. In the **Choose an action** dialog box, search for **Variables** and select **Initialize variable**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/19.png 'Power Automate dialog box')

6. In the **Initialize variable** action, update it with following details.

    - **Name**: `varEventsTable`
    - **Type**: `String`
    - **Value**: ```<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 2px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
<table>
<thead>
  <tr>
    <th>Session Title</th>
    <th>Description</th>
    <th>Session Date</th>
<th>Days away</th>
  </tr>
  </thead>
<tbody>```

    ![Screenshot of the Power Automate action with the details filled in](images/20.png 'Power Automate action')

7. Click **+ New step**.

8. In the **Choose an action** dialog box, search for **Dataverse** and select **List rows**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/21.png 'Power Automate dialog box')

9. In the **List rows** action, update it with following details.

    - **Table name**: `Community Events`
    - **Filter rows**: `Session Status eq 'Approved'`

    ![Screenshot of the Power Automate action with the details filled in](images/22.png 'Power Automate action')

10. Click **+ New step**.

11. In the **Choose an action** dialog box, search for **Control** and select **Apply to each**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/23.png 'Power Automate dialog box')

12. In the **Apply to each** action, update it with following details.

    - **Select an output from previous steps**: `Add the dynamic content value from the List rows action`

    ![Screenshot of the Power Automate action with the details filled in](images/24.png 'Power Automate action')

13. Click **+ New step** inside the **Apply to each** action.

14. In the **Choose an action** dialog box, search for **Data Operations** and select **Compose**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/25.png 'Power Automate dialog box')

15. In the **Compose** action, update it with following details.

    - **Inputs**: `Click on expressions and add the following expression:` ```div(sub(ticks(formatDateTime(items('Apply_to_each')?['cr9be_sessiondate'],'yyyy-MM-dd')), ticks(formatDateTime(utcNow(),'yyyy-MM-dd'))),864000000000)```

    ![Screenshot of the Power Automate action with the details filled in](images/26.png 'Power Automate action')

16. Click **+ New step** inside the **Apply to each** action.

17. In the **Choose an action** dialog box, search for **Control** and select **Condition**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/27.png 'Power Automate dialog box')

18. In the **Condition** action, update it with following details.

    - **Choose a value**: `Click on expressions and add the following expression:` ```int(outputs('Difference_in_days'))```
    - **is greater than**: '0'
    - **Choose a value**: `Click on expressions and add the following expression:` ```int(outputs('Difference_in_days'))```
    - **is less than or equal to**: '15'

    ![Screenshot of the Power Automate action with the details filled in](images/28.png 'Power Automate action')

19. Click **Add an action** inside the **If yes** branch of the **Condition** action.

20. In the **Choose an action** dialog box, search for **Data Operations** and select **Append to string variable**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/29.png 'Power Automate dialog box')

21. In the **Append to string variable** action, update it with following details.

    - **Name**: `varEventsTable`
    - **Value**: ```Click on expressions and add the following expression```: ```<tr style"background-color: #e1e1e1">
    <td>@{items('Apply_to_each')?['cr9be_sessiontitle']}</td>
    <td>@{items('Apply_to_each')?['cr9be_description']}</td>
    <td>@{formatDateTime(items('Apply_to_each')?['cr9be_sessiondate'],'dd-MM-yyyy')}</td>
<td>@{outputs('Difference_in_days')} days</td>
  </tr>```

    ![Screenshot of the Power Automate action with the details filled in](images/30.png 'Power Automate action')

22. Click **Add an action** outside the **Apply to each** action. Search for **Variable** and select **Apppend to string variable**

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/31.png 'Power Automate dialog box')

23. In the **Append to string variable** action, update it with following details.

    - **Name**: ```varEventsTable```
    - **Value**: ```Click on expressions and add the following expression```: ```</tbody></table>```

    ![Screenshot of the Power Automate action with the details filled in](images/32.png 'Power Automate action')

24. Click **+ New step**.

25. In the **Choose an action** dialog box, search for **Office 365 Outlook** and select **Send an email (V2)**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/33.png 'Power Automate dialog box')

26. In the **Send an email (V2)** action, update it with following details.

    - **To**: ```Click on dynamic content and add the following```: ```'Dynamic Content of the community memebers email''```
    - **Subject**: ```Click on expressions and add the following expression```: ```'Community Events in next 15 days'```
    - **Body**: ```Click on dynamic content and add the following```: ```variables('varEventsTable')```
    - **Is HTML**: ```Yes```

    ![Screenshot of the Power Automate action with the details filled in](images/34.png 'Power Automate action')

27. Click **Save**.

### Milestone 3: Create a Sign up flow for the community members

In this milestone, you'll create a Power Automate flow that will allow the community members to sign up for the events.

1. Click **+ New** in the top navigation bar of the solution. Hover over **Automate** and hover over **Cloud Flow**. Select **Automated**.

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/35.png 'Power Automate dialog box')

2. In the pop-up dialog box, add the following details.

    - **Name**: ```Sign up for Community Events```
    - **Trigger**: `When a HTTP request is received`

    ![Screenshot of the Power Automate dialog box with the SQL - Insert row option highlighted](images/36.png 'Power Automate dialog box')

